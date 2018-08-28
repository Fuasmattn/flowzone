<template>
  <div class="base-view">
   <h1>FlowZone</h1>
   <skill-chart></skill-chart>
  </div>
</template>

<script>
import SkillChart from './SkillChart';
export default {
  name: 'BaseView',
  props: {
    msg: String
  },
  components: {
    SkillChart
  }
  
}
</script>

<style scoped>

.base-view {
  width: 90%;
  height: 90%;
  margin: 0 auto;
  background-color: beige;
}

.svg {
  width: 800px;
  height: 600px;
}
</style>
