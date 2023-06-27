
<script>
export default {
  name: 'WorkCard',
  props:{
    work: Object,
  },
  methods:{
    formatData(dateString){
        const d = new Date(dateString);
        return d.toLocaleDateString();
    }
  }

}
</script>

<template>
  
    <div class="card" style="width: 15rem;">
      <img :src="work.image" :alt="work.title" style=" height: 200px; width: 100%;">
      <div class="card-body">
        <h5 class="card-title">{{ work.title }}</h5>
        <p class="my-2">Creato il: {{ formatData(work.creation_date) }}</p>
        <div class="my-1" v-if="work.type">
          <span class="badge text-bg-primary">{{ work.type.name }}</span>
        </div>
        <div>                  
          <span 
            v-for="technology in work.technologies" 
            :key="technology.id" 
            class="badge text-bg-warning my-1 me-1"
          >
            {{ technology.name }}
          </span>
        </div>

      </div>
    </div>

</template>

<style lang="scss" scoped>

@use '../scss/style.scss' as *;

.card{
  margin: 20px 10px;
  border: 2px solid black !important;
  .card-body{
    padding: 5px;
  }
}

</style>