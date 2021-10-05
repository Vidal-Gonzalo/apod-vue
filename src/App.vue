<template>
  <div id="app">
    <router-view/>
    <Footer/>
  </div>
</template>

<script>
  import Footer from '@/components/Footer.vue'

  export default {
    name: 'App',
    components: {
      Footer
    }
  }
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}


</style>
