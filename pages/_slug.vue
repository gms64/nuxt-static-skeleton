<template>
    <div class="container-fluid">
        <article>
            <h1 class="m20">{{ page.title }}</h1>
            <hr>
            <nuxt-content :document="page" />
        </article>
    </div>

</template>

<script>
export default {
  head() {
      return {
      title: (this.page.seo_title || this.page.title) + ' | ' + this.siteName,
      meta: [
          { hid: 'description', 
          name: 'description',
          content: (this.page.seo_desc || this.page.preview) }
      ]
      }
  },
  async asyncData({ $content, params, error, env }) {
    try {
      // Create pages for all documents found in the pages folder 
      const siteName = env.SITE_NAME
      const page = await $content('pages',params.slug).fetch()
      return {
        page,
        siteName
      }
    } catch {
      // If there is an error, create a 404 page
      error({ statusCode: 404, message: 'Page not found' })
    }
    
  }
}
</script>

