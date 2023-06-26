<script>

import  {store} from './store/store.js';
import axios from 'axios';

export default {
    name: 'home',

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

    <h1>Elenco Works</h1>

    <ul>
      <li 
        v-for="work in works" 
        :key="work.id"
      >
        <span>{{ work.title }}</span> -
        <strong>{{formatData(work.creation_date)}}</strong>

        

      </li>
    </ul>


  </div>

</template>

<style lang="scss" scoped>
@use './scss/style.scss' as *;

</style>

