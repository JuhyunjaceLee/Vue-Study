<template>
  <main>
    <div class="container py-4">
      <PostCreate @create-post="createPost"></PostCreate>

      <hr class="my-4" />

      <div class="row g-3">
        <div v-for="post in posts" :key="post.id" class="col col-4">
          <AppCard
            :title="post.title"
            :contents="post.contents"
            :badge="post.badge"
            :is-like="post.isLike"
            @toggle-like="post.isLike = !post.isLike"
            :post="post"
          ></AppCard>
          <button @click="post.isLike = !post.isLike">LIKE</button>
          <!-- <button @click="likeHandler()">LIKE</button> -->
        </div>
      </div>

      <hr class="my-4" />
      <!-- v-model 구현 가능
        (props)modelValue
        (event)update: mdelValue
      -->
      <!-- <LabelInput
        :model-value="username"
        @update:model-value="(value) => (username = value)"
      ></LabelInput> -->
      <LabelInput v-model="username" label="NAME"></LabelInput>
      <LabeITitle v-model:title="username" label="TITLE"></LabeITitle>
      <UserName
        v-model:firstname="firstname"
        v-model:lastname="lastname"
      ></UserName>
    </div>
  </main>
</template>

<script>
import AppCard from "@/components/AppCard.vue";
import PostCreate from "@/components/PostCreate.vue";
import LabelInput from "@/components/LabelInput.vue";
import LabeITitle from "./LabeITitle.vue";
import { ref } from "vue";
import UserName from "./UserName.vue";

export default {
  components: {
    AppCard,
    PostCreate,
    LabelInput,
    LabeITitle,
    UserName,
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
    const createPost = (newPost) => {
      // console.log("newPost", newPost);
      console.log("POSTS", typeof posts);
      posts.value.push(newPost);
    };

    const username = ref("");
    const firstname = ref("");
    const lastname = ref("");

    return {
      post,
      posts,
      username,
      firstname,
      lastname,
      likeHandler,
      createPost,
    };
  },
};
</script>

<style lang="scss" scoped></style>
