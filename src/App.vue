<template>
  <NewIndex />
</template>

<script>
import NewIndex from './components/index.vue'

export default {
  name: 'App',
  components: {
    NewIndex
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin:0;
  padding:0;
    /* background: #d2eaf1; */
  height: 100vh;
  width: 100vw;
}
</style>
