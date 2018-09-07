<template>
 <div class="title">
 <h1>{{title}}</h1>
 
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
 background-color: #2274A5;
 color: white;
 margin-bottom: 20px;
}
</style>