<template>
  <div>
    <Header :menuChecked="menuChecked" @changeMenuStatus="menuChecked=false" />

    <div class='main-content'>
      <nuxt />
    </div>
    
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";


export default {
  components: {
    Header,
    Footer
  },
  data() {
    return {
      menuChecked: false
    }
  }
}
</script>
