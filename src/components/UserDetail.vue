<template>
  <div class="component">
    <h3>You may view the User Details here</h3>
    <p>Many Details</p>
    <p>User Name: {{switchName()}}</p>
    <p>User Age is: {{userAge}}</p>
    <button @click="resetName()">Reset Name</button>
    <button @click="resetFn()">Reset Name via function</button>
  </div>
</template>

<script>
import { eventBus } from "../main";
export default {
  props: {
    myName: {
      type: String,
      default: "Some Name"
    },
    resetFn: Function,
    userAge: Number
  },
  methods: {
    switchName() {
      return this.myName;
    },
    resetName() {
      this.myName = "Krutika";
      this.$emit("nameWasReset", this.myName);
    },
    created() {
      eventBus.$on("ageWasEditted", age => {
        this.userAge = age;
        console.log("ageWasEditted detected");
      });
    }
  }
};
</script>

<style scoped>
div {
  background-color: lightcoral;
}
</style>
