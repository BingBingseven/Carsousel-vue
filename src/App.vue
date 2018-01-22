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
#app,ul,li {
  margin: 0;
  padding:0;
}
#app{
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align:center;
  width: 100%;
  height: 281px;
  overflow: hidden;
  position: relative;
}
li{
  list-style:none;
}
</style>
