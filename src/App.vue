<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/spiderIcon.png">
    <spiderCountTable></spiderCountTable>
  </div>
</template>

<script>

import spiderCountTable from './components/spiderCountTable.vue'

export default {
  name: 'app',
  components: {
    spiderCountTable
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
