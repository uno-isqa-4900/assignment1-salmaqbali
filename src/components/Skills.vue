<script setup>
import IconMinus from "./icons/IconMinus.vue";
</script>
<script>
export default {
  data() {
    return {
      newSkill: "",
      skills: ["Vue.js", "Frontend Developer"],
    };
  },
  methods: {
    addSkill() {
      console.log("called");
      if (this.newSkill.trim() != "") this.skills.push(this.newSkill);
      this.newSkill = "";
    },
    removeSkill(skillToBeDeleted) {
      this.skills = this.skills.filter((skill) => skill !== skillToBeDeleted);
    },
  },
};
</script>

<template>
  <div class="skills">
    <div class="inputContainer">
      <input
        type="text"
        v-model="newSkill"
        v-on:keypress.enter="addSkill()"
        placeholder="Enter your skill you have"
      />
    </div>
    <div v-for="(item, index) in skills" class="todoContainer">
      <div class="todoItem">
        <p>{{ index + 1 }}. {{ item }} {{ message }}</p>
        <span v-on:click="removeSkill(item)">
          <IconMinus onclick="" />
        </span>
      </div>
    </div>
  </div>
</template>

<style>
.skills {
  width: 600px;
  margin: 300px auto;
}
.inputContainer {
  background-color: #f7f7f7;
  color: #333333;
  padding: 20px;
}
.todoContainer {
  background-color: #b1b1b1;
}
.todo {
  border-radius: 5px;
  width: 400px;
  background-color: #f2f2f2;
  padding: 20px;
}
input {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}
.todoItem {
  display: flex;
  justify-content: space-between;
  padding: 10px 20px;
  color: #333333;
  border-bottom: 2px solid rgb(44, 44, 44);
}
</style>
