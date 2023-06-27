<script>
import  {store} from '../store/store';
import axios from 'axios';
import WorkCard from '../components/WorkCard.vue'

export default {
  name: 'Works',
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
      types:[],        
      technologies:[],   
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
          })
      },
      
      getTypes(){
        axios.get(store.apiUrl + 'works/types')
        .then(result =>{
          this.types = result.data;
        })
      },

      getTechnologies(){
        axios.get(store.apiUrl + 'works/technologies')
        .then(result =>{
          this.technologies = result.data;
        })
      },

      getWorkType(id){
        this.getApi(store.apiUrl + 'works/work-type/'+id)
      },

      getWorkTechnology(id){
        this.getApi(store.apiUrl + 'works/work-technology/'+id)
      }

  },
  mounted(){
      this.getApi(store.apiUrl + 'works');
      this.getTypes();
      this.getTechnologies();
  }

}
</script>

<template>
  <div class=" container d-flex">
    <div class="left w-100">
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

    <div class="right pt-5">
      <div>
        <h3>Tipi</h3>
        <button 
          v-for="type in types" 
          :key="type.id" 
          class="nv_button btn-type"
          @click="getWorkType(type.id)"
        >
          {{ type.name }}
        </button>
      </div>

      <div class="pt-2">
        <h3>Tecnologie</h3>
        <button 
        v-for="technology in technologies" 
        :key="technology.id" 
        class="nv_button btn-tech" 
        @click="getWorkTechnology(technology.id)"
        >{{ technology.name }}
      </button>
      </div>      
      
    </div>  
  </div> 
  
</template>

<style lang="scss" scoped>
@use '../scss/style.scss' as *;
.right{
  width: 250px;
  border-left: 1px solid lightgray;
  padding: 0 10px;
  .nv_button{
    border: 2px solid black;
    border-radius: 5px;
    padding: 5px 7px;
    font-weight: bold;
    margin-right: 5px;
    margin-bottom: 5px;
  }
  .btn-type{
      background-color: #0D6EFD;
      color: white;
    }
    .btn-tech{
      background-color: #FFC107;
      color: black;
    }
}

</style>