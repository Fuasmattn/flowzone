<template>
  <div class="base-view">
<div class="md-layout md-gutter">
  <div class="md-layout-item">
        <md-card >
          <md-card-content>
             <md-field>
              <label>Add Team Member</label>
                <md-input v-model="newMember" @keyup.enter="addNewMember"></md-input>
            </md-field>
                <member-stack-list :members="members"></member-stack-list>
          </md-card-content>
        </md-card>
    </div>
    <div class="sm-layout-item">
        <md-card >
          <md-card-content>
            <md-field>
              <label>Add Skill</label>
                <md-input v-model="newEntry" @keyup.enter="addNewSkill"></md-input>
            </md-field>
            <skill-stack-list :skill-colors="skillColors" :ready="ready" :active="activeSkill" :skills="skills"></skill-stack-list>
         </md-card-content>
        </md-card>
    </div>
    
    <div class="md-layout-item">
      <skill-chart v-if="ready" :skill-colors="skillColors" @nextSkill="onNextSkill" :active="activeSkill" :skills="skills"></skill-chart>
    </div>
  </div>
   
  

  </div>
</template>

<script>
import SkillChart from "./SkillChart";
import SkillStackList from "./SkillStackList";
import MemberStackList from './MemberStackList';
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
      skills: [{ id: 0, name: "Scrum" }],
      members: []
    };
  },
  components: {
    SkillChart,
    SkillStackList,
    MemberStackList
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
  width: 90%;
  height: 90%;
  margin: 0 auto;
}

.detached-card {
  margin-top: -100px;
}

.container {
  display: inline-block;
}

.svg {
  width: 800px;
  height: 600px;
}
</style>
