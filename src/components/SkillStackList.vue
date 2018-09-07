<template>
<div class="skill-stack-list">
 <ul>
  <li v-for="{id, name} in skills" :key="id" :style="{'color': active === id && ready ? skillColors[id]: 'black'}" :class="{active: active === id && ready}">
    {{ name }}
  </li>
 </ul>
</div>
</template>

<script>
 export default {
  name: 'SkillStackList',
  props: {
    ready: {
      type: Boolean,
      required: true
    },
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
  
}
.skill-stack-list > ul {
  list-style-type: none;
  padding-left: 0;
}

.skill-stack-list > ul > li {
  opacity: .3;
  min-width: 100px;
  padding: 8px 15px;
  font-weight: bold;
}
.skill-stack-list > ul > li.active {
  transition: all 800ms;
  opacity: 1;
}
</style>