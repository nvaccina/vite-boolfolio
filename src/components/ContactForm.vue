<script>
export default {
  name:'ContactForm'

}
</script>

<template>

  <form>
    <div>
      <input type="text" name="name" placeholder="Nome" class="w-100 p-1">
    </div>
    <div>
      <input type="email" name="mail" placeholder="Email" class="w-100 p-1 my-3">
    </div>
    <div>
      <textarea name="text" placeholder="Messaggio" cols="40" rows="10" class="w-100 p-1"></textarea>
    </div>
    <button class="btn btn-success px-5 mt-3" type="submit">Invia</button>
  </form>

  
  
</template>

<style lang="scss" scoped>
@use '../scss/style.scss' as *;

form{
  width: 500px;
  margin: 0 auto;
  text-align: center;
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

</style>