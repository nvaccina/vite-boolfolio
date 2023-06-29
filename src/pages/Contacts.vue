<script>
import ContactForm from '../components/ContactForm.vue';
export default {
  name: 'Contacts',
  components:{
    ContactForm
  }

}
</script>

<template>
  <div class="container">
    <h1 class="pb-2">Contatti</h1>

    <ContactForm/>

  </div>  
</template>

<style lang="scss" scoped>
@use '../scss/style.scss' as *;

</style>