<template>
    <div class="container-fluid">
        <nuxt-link to='/blog'>Back to Blog</nuxt-link>
        <article>
            <h1 class="m20">{{ article.title }}</h1>
            <p><em>{{ article.createdAt  | moment("MMMM Do, YYYY") }}</em></p>
            <hr>

            <nuxt-content :document="article" />
            <prev-next :prev="prev" :next="next" />
        </article>
    </div>
</template>


<script>
import VueMoment from 'vue-moment'
import PrevNext from "~/components/PrevNext.vue"

  export default {
    components: {
        PrevNext
    },
    head() {
        return {
        title: (this.article.seo_title || this.article.title) + ' | ' + this.siteName,
        meta: [
            { hid: 'description', 
            name: 'description',
            content: (this.article.seo_desc || this.article.preview) }
        ]
        }
    },
    async asyncData({ $content, params, error, env }) {
        try {
            const siteName = env.SITE_NAME
            const article = await $content('posts', params.slug).fetch()

            const [prev, next] = await $content('posts')
            .only(['title', 'slug'])
            .sortBy('createdAt', 'desc')
            .surround(params.slug)
            .fetch()

            return {
            article,
            prev,
            next,
            siteName
            }
        } catch {
            error({ statusCode: 404, message: 'Page not found' })
        }
    },
    methods: {
        formatDate(date) {
        const options = { year: 'numeric', month: 'long', day: 'numeric' }
        return new Date(date).toLocaleDateString('en', options)
        }
    }
  }
</script>
