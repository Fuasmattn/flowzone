<template>
<div class="skill-stack-list">
 <ul>
  <li v-for="{id, name} in skills" :key="id" :style="{'background-color': active === id ? skillColors[id]: 'transparent'}" :class="{active: active === id}">
    {{ name }}
  </li>
 </ul>
</div>
</template>

<script>
 export default {
  name: 'SkillStackList',
  props: {
   skills: {
    type: Array,
    required: true,
   },
   skillColors: {
    type: Array,
    required: true,
   },
   active: {
     type: Number,
     required: true,
     default: 0
   }
  }
 }
</script>

<style>
.skill-stack-list {
  vertical-align: top;
  display: inline-block;
}
.skill-stack-list > ul {
  list-style-type: none;
}

li {
  opacity: .3;
  width: 100px;
  padding: 5px 15px;
  border-radius: 50px;
}
li.active {
  opacity: 1;
  font-weight: bold;
  background-color: lightgreen;
}
</style>