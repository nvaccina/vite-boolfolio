<script>

import  {store} from './store/store.js';
import axios from 'axios';
import WorkCard from './components/WorkCard.vue'

export default {
    name: 'home',
    components:{
      WorkCard,
    },

    data(){
        return{
            works:[],
        }
    },

    methods:{
        getApi(){
            axios.get(store.apiUrl + 'works')
            .then(results => {
                this.works = results.data;
            })
        },

        formatData(dateString){
          const dd = new Date(dateString);
          return dd.toLocaleDateString();
        }
    },

    mounted(){
        this.getApi();
    }

}
</script>

<template>
  <div class="container">

    <h1 class="py-3">Elenco Works</h1>

    <div class="d-flex flex-wrap justify-content-center">
      <WorkCard
        v-for="(work, index) in works"
        :key="index"
        :image="work.image"
        :title="work.title"
        :type="work.type"
        :technologies="work.technologies"
        :text="work.text"
      />

    </div>


  </div>

</template>

<style lang="scss" scoped>
@use './scss/style.scss' as *;

</style>

