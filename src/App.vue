<template>
  <div id="app">
    <vMain />
  </div>
</template>

<script>
import vMain from './components/main.vue';


export default {
  name: 'App',
  components: {
    vMain
  }
}
</script>

<style>
#app {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
