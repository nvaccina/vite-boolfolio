
<script>
export default {
  name: 'WorkCard',
  props:{
    work: Object,
  },

}
</script>

<template>
  
    <div class="card m-2" style="width: 15rem;">
      <img :src="work.image" :alt="work.title" style=" height: 200px; width: 100%;">
      <div class="card-body">
        <h5 class="card-title">{{ work.title }}</h5>
        <span v-html="work.text" class="card-text mb-2"></span>
        <div class="m-1" v-if="work.type">
          <span class="badge text-bg-primary">{{ work.type.name }}</span>
        </div>
        <div>                  
          <span 
            v-for="technology in work.technologies" 
            :key="technology.id" 
            class="badge text-bg-secondary m-1"
          >
            {{ technology.name }}
          </span>
        </div>

      </div>
    </div>

</template>

<style lang="scss" scoped>

@use '../scss/style.scss' as *;

</style>