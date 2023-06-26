
<script>
export default {
  name: 'WorkCard',
  props:{
    image: String,
    title: String,
    type: Object,
    technologies: Array,
    text: String,
  },

}
</script>

<template>
  

    <div class="card m-2" style="width: 15rem;">
      <img :src="image" :alt="title" style=" height: 200px; width: 100%;">
      <div class="card-body">
        <h3 class="card-title">{{ title }}</h3>
        <p v-html="text" class="card-text"></p>
        <span class="badge text-bg-primary">TIpo:</span>
      </div>
    </div>



  
</template>

<style>

</style>