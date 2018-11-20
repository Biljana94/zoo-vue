<template>
  <div id="app">
    <Zoo /> <!--dodajemo komponentu Zoo.vue-->
  </div>
</template>

<script>
import Zoo from './components/Zoo.vue' //importujemo komponentu

export default {
  name: 'app',
  components: {
    Zoo //dodajemo komponentu u listu komponenata
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
