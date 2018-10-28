<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div><router-link to="/">test</router-link> |
    <router-link to="/Home">test2</router-link> |
    <router-link to="/Blank">blank</router-link></div>
    <router-view/>



  </div>
</template>

<script>
export default {
  name: 'App',
        data() {
            return {
                test1: "Hello World"
            }
        }
  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
