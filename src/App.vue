<script setup>
import { ref } from "vue";
import BlogPost from "./components/BlogPost.vue";

const postsData = ref([
  {
    id: 1,
    title: "Post 1",
    body: "Description 1",
  },
  {
    id: 2,
    title: "Post 2",
    body: "Description 2",
  },
  {
    id: 3,
    title: "Post 3",
    body: "Description 3",
  },
  {
    id: 4,
    title: "Post 4",
    body: "Description 4",
  },
]);

const favoritoref = ref("");

const fijarFavorito = (title) => {
  favoritoref.value = title;
};
</script>

<template>
  <div class="container">
    <h1>APP RONNY</h1>
    <h2>MI FAVORTITE IS {{ favoritoref }}</h2>
    <BlogPost
      v-for="post in postsData"
      :key="post.title"
      :title="post.title"
      :id="post.id"
      :body="post.body"
      class="mb-2"
      :fijarFavorito="fijarFavorito"
    />
  </div>
</template>
