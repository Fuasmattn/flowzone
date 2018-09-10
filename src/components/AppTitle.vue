<template>
 <div class="title">
 <h1>{{title}}</h1>
 <div>
  <md-button class="md-raised md-primary">Next Member</md-button>
 </div>
 
 </div>
</template>

<script>
 export default {
  name: 'AppTitle',
  props: {
   title: String
  }
 }
</script>

<style scoped>
.title {
 padding: 30px;
 height: 200px;
 background-color: rgb(24, 13, 59);
 color: white;
 margin-bottom: 20px;
}
</style>