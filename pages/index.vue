<template>
  <div class="home-container">
    <div class="u-full-width">
      <h1 class="site-title">
          <!-- Define Custom Site title or completely change the page -->
          nuxt<span class="txt-color"> static </span>skeleton
      </h1>
      <p>
        Starter Template for a Nuxt-based Blog
      </p>
      <a class="no-highlighter" href="https://github.com/gms64/nuxt-static-skeleton" target="_blank">
        <button class="button-primary">
          See the Repo
        </button>
      </a>

    </div>
    <!-- This is used to load the netlify identity widget so you can use Netlify CMS -->
    <script async src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
  </div>
</template>

<script>
export default {
  // Define SEO Variables / Site Title, etc.
  head() {
    return {
      title: this.siteName || 'Home Page',
      meta: [
      { hid: 'description',
      name: 'description',
      content: 'A website created with Nuxt Static Skeleton' }
      ]
    };
  },
  async asyncData({ env }) {
    const siteName = env.SITE_NAME
    return {
      siteName
    }
  }
}
</script>

