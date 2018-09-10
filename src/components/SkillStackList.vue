<template>
<div class="skill-stack-list">
   <md-chip v-for="{id, name} in skills" :key="id" class="chip" :style="{'background-color': active === id && ready ? skillColors[id]: ''}" :class="{active: active === id && ready}" md-deletable>{{name}}</md-chip>
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
}
.skill-stack-list > ul > li.active {
  opacity: 1;
  border: 1px solid;
}
.chip {
  margin-bottom: 5px;
  background-color: rgba(255,255,255,.2);
}

</style>