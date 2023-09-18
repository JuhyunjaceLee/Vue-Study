<template>
  <div>
    <button v-on:click="addMessage">+</button>
    <p>{{ message }}</p>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const message = ref("Hello");
    const addMessage = () => {
      message.value = message.value + "!";
    };
    console.log(message);
    console.log(message.value);
    console.log(typeof message.value);
    return {
      message,
      addMessage,
    };
  },
};
</script>

<style lang="scss" scoped></style>
