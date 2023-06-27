
<script>
export default {
  name: 'WorkCard',
  props:{
    work: Object,
  },
  computed:{
    formattedData(){
        const d = new Date(this.work.creation_date);
        const options = {
          weekday: "long",
          year: "numeric",
          month: "long",
          day: "numeric",
        };
        function getUserLocale(){
            const userLocale = navigator.languages && navigator.languages.length
            ? navigator.languages[0]
            : navigator.language;

	          return userLocale;
	      }

        return d.toLocaleString(getUserLocale(), options);
    }
  }

}
</script>

<template>
  
    <div class="card" style="width: 15rem;">
      <img :src="work.image" :alt="work.title" style=" height: 200px; width: 100%;">
      <div class="card-body">
        <h5 class="card-title">{{ work.title }}</h5>
        <p class="my-2">Creato: {{ formattedData }}</p>
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