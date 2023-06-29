<script>
import  {store} from '../store/store';
import axios from 'axios';

export default {
  name:'ContactForm',
  data(){
    return{
      name:'',
      email:'',
      message:'',
      errors: {}
    }
  },
  methods:{
    sendForm(){
      const data = {
        name: this.name,
        email: this.email,
        message: this.message,
      }
      axios.post(`${store.apiUrl}contacts`, data)
        .then(result => {

          if(!result.data.success){
            this.errors = result.data.errors;
          }else{
            this.errors = {};
          }
        })
      
    }
  }

}
</script>

<template>

  <form @submit.prevent="sendForm()">
    <div>
      <input v-model.trim="name" type="text" name="name" placeholder="Nome" :class="{'error-form' : errors.name}" class="w-100 p-1">
      <p class="error-msg" v-for="(error, index) in errors.name" :key="index">{{ error }}</p>
    </div>
    <div>
      <input v-model.trim="email" type="email" name="email" placeholder="Email" :class="{'error-form' : errors.email}" class="w-100 p-1 my-2">
      <p class="error-msg" v-for="(error, index) in errors.email" :key="index">{{ error }}</p>
    </div>
    <div>
      <textarea  v-model.trim="message" name="text" placeholder="Messaggio" cols="40" rows="10" :class="{'error-form' : errors.message}" class="w-100 p-1"></textarea>
      <p class="error-msg" v-for="(error, index) in errors.message" :key="index">{{ error }}</p>
    </div>
    <div class="text-center">
      <button class="btn btn-success px-5 mt-3" type="submit">Invia</button>
    </div>
    
  </form>

  
  
</template>

<style lang="scss" scoped>
@use '../scss/style.scss' as *;

form{
  width: 500px;
  margin: 0 auto;
  input, textarea{
    border: 1px solid grey;
    border-radius: 5px;
  }
  button{
    border-radius: 5px;
    font-weight: bold;
    text-transform: uppercase;
  }
}
.error-form{
  border: 1px solid red;
}
.error-msg{
  color: red;
}


</style>