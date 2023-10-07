<template>
  <div>
    <TheNav></TheNav>
    <TheView></TheView>
  </div>
</template>

<script>
import TheNav from "./components/TheNav.vue";
import TheView from "./components/TheView.vue";
import "@/assets/base.css";
export default {
  components: {
    TheNav,
    TheView,
  },
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped></style>
