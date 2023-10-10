<template>
  <div class="card">
    <div class="card-body">
      <!-- {{ $props }} -->
      <!-- type: news, notice -->
      <span class="badge bg-secondary">{{ badgeName }}</span>
      <h5 class="card-title red mt-2">{{ title }}</h5>
      <p class="card-text" :class="$style.red">
        {{ contents }}
      </p>
      <a href="#" class="btn" :class="isLikeClass" @click="toggleLike()"
        >좋아요</a
      >
    </div>
  </div>
</template>

<script>
console.log("AppCard Module");
import { computed } from "vue";

export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    contents: {
      type: String,
      // required: true,
    },
    badge: {
      type: String,
      default: "NEWS",
      // validator: (value) => {
      //   return ["NEWS", "NOTICE"].includes(value);
      // },
    },
    isLike: {
      type: Boolean,
      default: false,
    },
    post: {
      type: Object,
    },
  },
  emits: ["toggleLike"],
  setup(props, context) {
    console.log("AppCard Setup");
    //AppCard 인스턴스가 6번 생성되었기 때문에 콘솔도 6번 찍힘.
    const badgeName = computed(() =>
      props.badge === "NEWS" ? "NEWS" : "NOTICE"
    );
    const isLikeClass = computed(() =>
      props.isLike ? "btn-danger" : "btn-outline-danger"
    );
    const toggleLike = () => {
      context.emit("toggleLike");
    };
    return { isLikeClass, badgeName, toggleLike };
  },
};
</script>

<style module>
.red {
  color: grey !important;
}
</style>
