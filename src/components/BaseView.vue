<template>
  <div class="base-view">
   <h1>FlowZone</h1>
   <div class="container">
    <skill-stack-list :skill-colors="skillColors" :active="activeSkill" :skills="skills"></skill-stack-list>
    <skill-chart :skill-colors="skillColors" @nextSkill="onNextSkill" :active="activeSkill" :skills="skills"></skill-chart>
   </div>
  </div>
</template>

<script>
import SkillChart from './SkillChart';
import SkillStackList from './SkillStackList';
export default {
  name: 'BaseView',
  props: {
    msg: String
  },
  data() {
    return {
      activeSkill: 0,
      skillColors: ['#E5F9E0', '#A3F7B5', '#40C9A2', '#2F9C95', '#664147', '#2274A5', '#8A6552', '#9D8420'],
      skills: [{id: 0, name: 'Scrum'}, {id: 1, name: 'MongoDB'}, {id: 2, name: 'Angular'}, {id: 3, name: 'React-Native'}, {id: 4, name: 'Vue'}, {id: 5, name: 'Springboot'}, {id: 6, name: 'Payara'}, {id: 7, name: 'Kubernetes'} ]
    }
  },
  components: {
    SkillChart, SkillStackList
  },
  methods: {
    onNextSkill: function() {
      if(this.activeSkill !== this.skills.length) this.activeSkill++;
    }
  }
}
</script>

<style scoped>

.base-view {
  width: 90%;
  height: 90%;
  margin: 0 auto;
}

.container {
  display: inline-block;
}

.svg {
  width: 800px;
  height: 600px;
}
</style>
