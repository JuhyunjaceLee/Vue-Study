<template>
  <div>
    <h2>보간법</h2>
    <p>{{ message }}</p>
    <p v-once>{{ message }}</p>
    <button v-on:click="message = message + '!'">+!</button>
    <hr />
    <h2>HTML</h2>
    <p>{{ rawhtml }}</p>
    <p v-html="rawhtml"></p>
    <hr />
    <h2>속성 바인딩</h2>
    <div v-bind:title="dynamicTitle">마우스를 올려보세요.</div>
    <input type="text" :value="inputValue" v-bind:disabled="isInputDisabled" />
    <input v-bind="attrs" />
    <h2>Javascript 표현식</h2>
    {{ message.split("").reverse().join("") }}<br />
    {{ isInputDisabled ? "YES" : "NO" }}
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const message = ref("안녕하세요!");
    const rawhtml = ref("<strong>안녕하세요</strong>");
    const dynamicTitle = ref("HI");
    const inputValue = ref("값을 입력하세요.");
    const isInputDisabled = ref(false);
    const attrs = {
      type: "text",
      value: "속성 값",
      disabled: true,
    };
    return {
      message,
      rawhtml,
      dynamicTitle,
      inputValue,
      isInputDisabled,
      attrs,
    };
  },
};
</script>

<style lang="scss" scoped></style>
