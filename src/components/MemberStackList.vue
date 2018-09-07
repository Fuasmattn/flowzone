<template>
 <div class="member-stack-list">
<ul>
  <li v-for="{name} in members" :key="name">
    {{ name }}
  </li>
 </ul>
 </div>
</template>

<script>
 export default {
  name: 'MemberStackList',
  props: {
   members: Array
  }
 }
</script>

<style>
.member-stack-list {
  vertical-align: top;
  
}
.member-stack-list > ul {
  list-style-type: none;
  padding-left: 0;
}

li {
  opacity: 1;
  min-width: 100px;
  padding: 8px 15px;
}

</style>