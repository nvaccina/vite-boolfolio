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
            links:[],
            first_page_url: null,
            last_page_url: null,
            current_page: null,
            last_page: null,            
        }
    },

    methods:{
        getApi(endpoint){
            axios.get(endpoint)
            .then(results => {
                this.works = results.data.data;
                this.links = results.data.links;
                this.first_page_url = results.data.first_page_url;
                this.last_page_url = results.data.last_page_url;
                this.current_page = results.data.current_page;
                this.last_page = results.data.last_page;
                console.log(this.current_page);
                console.log(this.works);
            })
        },

        formatData(dateString){
          const dd = new Date(dateString);
          return dd.toLocaleDateString();
        }
    },

    mounted(){
      this.getApi(store.apiUrl + 'works');
    }

}
</script>

<template>
  <div class="container my-5">

    <h1 class="py-3">Elenco Works</h1>

    <div class="d-flex flex-wrap justify-content-center">
      <WorkCard
        v-for="(work, index) in works"
        :key="index"
        :work="work"
      />
    </div>
    <div class="d-flex justify-content-center">
      <button 
        @click="getApi(first_page_url)" 
        :disabled="current_page === 1"
      >   
        <i class="fa-solid fa-backward-step"></i> 
      </button>

      <button 
        v-for="(link, index) in links" 
        :key="index" 
        @click="getApi(link.url)" 
        :disabled="link.active || !link.url"
        v-html="link.label"
      ></button>

      <button 
        @click="getApi(last_page_url)" 
        :disabled="current_page === last_page"
      > 
        <i class="fa-solid fa-forward-step"></i> 
      </button>

    </div>


  </div>

</template>

<style lang="scss" scoped>
@use './scss/style.scss' as *;

button{
  padding: 5px 10px;
  border: 1px solid lightgray;
  border-radius: 5px;
  margin: 0 5px;
}

</style>

