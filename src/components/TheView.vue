<template>
  <main>
    <div class="container py-4">
      <div class="row g-3">
        <div v-for="post in posts" :key="post.id" class="col col-4">
          <AppCard
            :title="post.title"
            :contents="post.contents"
            :badge="post.badge"
            :is-like="post.isLike"
            @toggle-like="post.isLike = !post.isLike"
          ></AppCard>
          <button @click="post.isLike = !post.isLike">LIKE</button>
          <!-- <button @click="likeHandler()">LIKE</button> -->
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import AppCard from "@/components/AppCard.vue";
import { ref } from "vue";

export default {
  components: {
    AppCard,
  },
  setup() {
    const post = ref({
      title: String,
      contents: String,
      badge: String,
      isLike: Boolean,
    });

    const posts = ref([
      {
        id: 1,
        title: "TITLE1",
        contents: "CONTENTS1",
        badge: "NEWS",
        isLike: true,
      },
      {
        id: 2,
        title: "TITLE2",
        contents: "CONTENTS2",
        badge: "NEWS",
        isLike: false,
      },
      {
        id: 3,
        title: "TITLE3",
        contents: "CONTENTS3",
        badge: "NOTICE",
        isLike: true,
      },
      {
        id: 4,
        title: "TITLE4",
        contents: "CONTENTS4",
        badge: "NEWS",
        isLike: true,
      },
      {
        id: 5,
        title: "TITLE5",
        contents: "CONTENTS5",
        badge: "NEWS",
        isLike: false,
      },
      {
        id: 6,
        title: "TITLE6",
        contents: "CONTENTS6",
        badge: "NOTICE",
        isLike: true,
      },
    ]);
    const likeHandler = () => {
      console.log(post);
    };
    return { post, posts, likeHandler };
  },
};
</script>

<style lang="scss" scoped></style>
