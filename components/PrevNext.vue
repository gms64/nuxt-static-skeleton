<template>
<div>
  <!-- Pagination for individual blog posts -->
  <hr class="mb0">
  <div class="row between-xs m20">
    <div class="col-xs-6 start-xs">
      <span v-if="prev">
        Previous: 
        <NuxtLink v-if="prev"
        :to="{ name: postTypeSlug, params: { slug: prev.slug } }"
      >
        {{ prev.title }}
      </NuxtLink>
      <span>&nbsp;</span>

      </span>
    </div>
    <div class="col-xs-6 end-xs">
        <span v-if="next">
          Next: 
          <NuxtLink
            v-if="next"
            :to="{ name: postTypeSlug, params: { slug: next.slug } }"
            
          >
            {{ next.title }}
          </NuxtLink>
        </span>
    </div>
  </div>
</div>
</template>

<script>
  export default {
    props: {
      prev: {
        type: Object,
        default: () => null
      },
      next: {
        type: Object,
        default: () => null
      },
      postTypeSlug: {
        type: String,
        default: 'blog-slug'
      }
    }
  }
</script>