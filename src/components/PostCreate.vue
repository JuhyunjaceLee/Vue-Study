<template>
  <div class="row g-3">
    <div class="col col-2">
      <select
        v-model="badge"
        class="form-select"
        aria-label="Default select example"
      >
        <option selected value="NEWS">NEWS</option>
        <option value="NOTICE">NOTICE</option>
      </select>
    </div>
    <div class="col col-8">
      <input v-model="title" type="text" class="form-control" />
    </div>
    <div class="col col-2 d-grid">
      <button class="btn btn-primary" @click="createPost">ADD</button>
    </div>
    <!-- @click="$emit('createPost', 1, 2, 3, '김길동')" -->
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  //vue3 emits 옵션
  // emit: ["createPost"],
  emits: {
    //유효성 체크 없는 경우, null
    //createPost: null
    createPost: (newPost) => {
      if (!newPost.badge) {
        return false;
      } else if (!newPost.title) {
        return false;
      }
      return true;
    },
  },

  setup(props, { emit }) {
    const badge = ref("NEWS");
    const title = ref("");
    const createPost = () => {
      const newPost = {
        badge: badge.value,
        title: title.value,
      };
      emit("createPost", newPost);
      badge.value = "NEWS";
      title.value = "";
    };
    return { badge, createPost, title };
  },
};
</script>

<style lang="scss" scoped></style>
