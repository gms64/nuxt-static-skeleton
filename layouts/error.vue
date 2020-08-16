<template>
  <div class="error-container">
    <div class="u-full-width">
    <h3 v-if="!!error.message">{{ error.message }}</h3>
    <h3 v-else-if="error.statusCode === 404">404 Page Not Found</h3>
    <h3 v-else>An error occurred</h3>
    <br>
    <img class="error-img" src="~/static/img/macintosh.svg" alt="illlustrations-macintosh">
    </div>
  </div>
</template>

<script>
export default {
  name: 'NuxtError',
  props: ['error'],
}
</script>

<style>
.error-container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.error-img {
    max-width: 25%;
    max-height: 25%;
}

</style>