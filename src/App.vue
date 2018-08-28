<template>
  <div id="app">
   <base-view></base-view>
  </div>
</template>

<script>
import BaseView from './components/BaseView.vue'

export default {
  name: 'app',
  components: {
    BaseView
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0;
  padding: 0;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
