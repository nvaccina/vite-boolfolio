<script>
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components:{
    Header,
    Footer
  }

}
</script>

<template>
  <Header/>

  <router-view></router-view>

  <Footer/>
  
</template>

<style lang="scss" scoped>
@use './scss/style.scss' as *;



</style>