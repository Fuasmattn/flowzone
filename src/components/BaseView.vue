<template>
  <div class="base-view">
    <div class="container chart">
      <skill-chart v-if="ready" :skill-colors="skillColors" @nextSkill="onNextSkill" :active="activeSkill" :skills="skills"></skill-chart>
    </div>
    <div class="title">
      <div class="container">
        <div class="md-layout md-gutter">
          <div class="md-layout-item">
             <md-field>
                <label>Add Team Member</label>
                  <md-input v-model="newMember" @keyup.enter="addNewMember"></md-input>
              </md-field>
              <member-stack-list :members="members"></member-stack-list>
                
          </div>
        <div class="md-layout-item">
           <md-field>
                <label>Add Skill</label>
                  <md-input v-model="newEntry" @keyup.enter="addNewSkill"></md-input>
              </md-field>  
          <skill-stack-list :skill-colors="skillColors" :ready="ready" :active="activeSkill" :skills="skills"></skill-stack-list>
        </div>
        <div class="md-layout-item">
          <md-button class="md-raised md-primary">Next Member</md-button>
        </div>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import SkillChart from "./SkillChart";
import MemberStackList from './MemberStackList';
import SkillStackList from './SkillStackList';

export default {
  name: "BaseView",
  props: {
    msg: String
  },
  data() {
    return {
      ready: true,
      newEntry: "",
      newMember: "",
      activeSkill: 0,
      skillColors: [
        "#40C9A2",
        "#2F9C95",
        "#664147",
        "#2274A5",
        "#8A6552",
        "#9D8420"
      ],
      skills: [{ id: 0, name: "Scrum" }, { id: 1, name: "Kubernetes" }],
      members: []
    };
  },
  components: {
    SkillChart,
    MemberStackList,
    SkillStackList
  },
  methods: {
    onNextSkill: function() {
      if (this.activeSkill !== this.skills.length) this.activeSkill++;
    },
    addNewSkill: function() {
      this.skills.push({ id: this.getNextId(), name: this.newEntry });
      this.newEntry = "";
    },
    addNewMember: function() {
      this.members.push({name: this.newMember });
      this.newMember = "";
    },
    getNextId: function() {
      return this.skills[this.skills.length - 1].id + 1;
    }
  }
};
</script>

<style scoped>
.base-view {

}

.title {
  width: 100%;
  padding: 30px;
  height: 400px;
  background-color: rgb(24, 13, 59);
  color: white;
}

.title > h1 {
  margin-bottom: 50px;
}

.container {
  width: 80%;
  margin: 0 auto;
}
.chart {
  padding-top: 100px;
}
</style>
