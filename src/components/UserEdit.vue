<template>
  <div class="component">
    <h3>You may edit the User here</h3>
    <p>Edit me!</p>
    <p>User age is : {{userAge}}</p>
    <button @click="resetAge()">Reset Age</button>
    <button @click="resetAgeFn()">Reset Age with callback</button>
    <button @click="eventBusReset()">Reset age using event bus</button>
  </div>
</template>

<script>
import { eventBus } from "../main";
export default {
  props: {
    userAge: Number,
    resetAgeFn: Function
  },
  methods: {
    resetAge() {
      this.userAge = 27;
      this.$emit("ageWasReset", this.userAge);
    },
    eventBusReset() {
      this.userAge = 21;
      eventBus.$emit("ageWasEditted", this.userAge);
      console.log("ageWasEditted emitted");
    }
  }
};
</script>

<style scoped>
div {
  background-color: lightgreen;
}
</style>
