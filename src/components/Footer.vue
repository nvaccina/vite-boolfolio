<script>
export default {
  name:'Footer'

}
</script>

<template>
  <footer class="mt-5">
    <div class="container-fluid d-flex justify-content-center align-items-center h-100">
      <strong>Made by Niccolò</strong>

    </div>
  </footer>
  
</template>

<style lang="scss" scoped>
@use '../scss/style.scss' as *;

footer{
  height: 80px;
  background-color: brown;
  border-top: 3px solid black;
}

</style>