<template>
    <header class="header">
      <nuxt-link to="/" class="logo">
        <!-- Update your site logo text -->
        nss
      </nuxt-link>
      <input class="menu-btn" type="checkbox" id="menu-btn" v-model="menuChecked"/>
      <label class="menu-icon" for="menu-btn"><span class="navicon"></span></label>
      <ul class="menu">
        <!-- Page Links -->
        <li><nuxt-link to="/blog" @click.native="menuChecked=false">blog</nuxt-link></li>
        <li><nuxt-link to="/contact" @click.native="menuChecked=false">contact</nuxt-link></li>
        <li><nuxt-link to="/about" @click.native="menuChecked=false">about</nuxt-link></li>
      </ul>
    </header>
</template>

<script>
export default {
    props: ['menuChecked']
}
</script>