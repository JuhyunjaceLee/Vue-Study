<template>
  <div>
    <p>
      {{ counter }}
    </p>
    <p>
      {{ message }}
    </p>
    <button v-on:click="increament">UP</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const counter = ref(0);
    const message = ref("Hello VUE3");
    const increament = () => {
      counter.value++;
    };
    return {
      counter,
      message,
      increament,
    };
  },
};
</script>

<style lang="scss" scoped></style>
