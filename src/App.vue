<template>
  <div id="app">
   <app-title title="kimmd no"/>
   <base-view></base-view>
  </div>
</template>

<script>
import BaseView from './components/BaseView.vue';
import AppTitle from './components/AppTitle.vue';

export default {
  name: 'app',
  components: {
    BaseView, AppTitle
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
