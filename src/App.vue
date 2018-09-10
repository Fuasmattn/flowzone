<template>
  <div id="app">
   <base-view></base-view>
  </div>
</template>

<script>
import BaseView from './components/BaseView.vue';


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
  margin: 0;
  padding: 0;
  color: #2c3e50;
  background-color: rgb(250, 250, 250);
}
</style>
