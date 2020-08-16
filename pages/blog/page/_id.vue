<template>
  <div class="container-fluid">
    <h1>Blog</h1>
    <hr>
    <div v-for="article of articles" :key="article.slug">
        <h3 class="mb10">
          <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
              {{ article.title }}
          </NuxtLink>
        </h3>
        <p><em>{{ (article.date || article.createdAt) | moment("MMMM Do, YYYY") }}</em></p>
        <p>{{ article.summary }}</p>
        <p><NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">Read More</NuxtLink></p>
        <br>
    </div>
    <PrevNextPg :prevPg="prevPg" :nextPg="nextPg"/>
  </div>

</template>

<script>
import VueMoment from 'vue-moment'
import PrevNextPg from "~/components/PrevNextPg.vue"

export default {
    components: {
        PrevNextPg
    },
  head() {
      return {
      // Adds a piped title if sitename is defined
      title: 'Blog' + (this.siteName ? ' | ' + this.siteName : ''),
      meta: [
          { hid: 'description', 
          name: 'description', 
          content: (this.siteName ? this.siteName + ' ' : '') + 'Blog' }
      ]
    }
  },
  async asyncData({ $content, params, env }) {
    const siteName = env.SITE_NAME
    // Retrieves current posts for the page.  
    // Also looks one page ahead to see if we should add a 'Next Page' link
    const postsPerPage = +env.POSTS_PER_PAGE || 5
    const pgNum = +params.id
    const prevPg = pgNum - 1
    const articles = await $content('posts')
      .only(['title', 'summary', 'slug','createdAt','date'])
      .sortBy('date', 'desc')
      .skip(postsPerPage*(pgNum-1))
      .limit(postsPerPage)
      .fetch()

    // Get the next group of articles after this page
    const nextArticles = await $content('posts')
      .only(['title', 'summary', 'slug','createdAt','date'])
      .sortBy('date', 'desc')
      .skip(postsPerPage*(pgNum))
      .limit(postsPerPage)
      .fetch()
    
    // nextPg is null unless there are articles after this page
    let nextPg = null
    if (nextArticles.length >= 1) {
        nextPg = pgNum + 1
    }

    // Returns current page articles, as well as the prevPg, nextPg, and pgNum vars
    return {
      articles,
      prevPg,
      nextPg,
      pgNum,
      siteName
    }
  }


}
</script>
