<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #142535;
  box-sizing: content-box;
}
button{
  background-color: #D2A599;
  box-shadow: 0 8px 16px 0 rgba(253, 239, 239, 0.503);
  border-radius: 5px;
  border-color: #000000;
}
button:hover {
  box-shadow: 0 3px 5px 0 #836953}

</style>
