<script>
export default {
  name:'Header',
}
</script>

<template>
  <header>
    <ul>
      <li>
        <router-link :to="{name:'home'}">home</router-link>
      </li>
      <li>
        <router-link :to="{name:'contacts'}">contatti</router-link>
      </li>
      <li>
        <router-link :to="{name:'works'}">works</router-link>
      </li>
      <li>
        <router-link :to="{name:'about'}">chi siamo</router-link>
      </li>
    </ul>
  </header>
  
</template>

<style lang="scss" scoped>
header{
  border-bottom: 2px solid red;
  ul{
    list-style: none;
    display: flex;
    justify-content: center;
    padding: 20px 0;
    margin: 0;
    li{
      margin: 0 10px;
      border-bottom: 2px solid white;
      &:hover, &.active{
          border-bottom: 2px solid blue;
        }
      a{
        text-transform: uppercase;
        text-decoration: none;
        color: red;
        font-size: 18px;
        font-weight: bold;
        &:hover, &.active{
          color: blue;
        }
      }
    }
  }
}


</style>