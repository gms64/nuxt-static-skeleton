<template>
  <div class="home-container">
    <div class="u-full-width">
      <h1 class="site-title">
          <!-- Define Custom Site title or completely change the page -->
          greg<span class="txt-color">/</span>data
      </h1>
      <p>
        infrequently updated musings of a confused developer / data scientist
      </p>
      <span class="sm-txt"><em>I wouldn't read too much into anything here...</em></span>

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

