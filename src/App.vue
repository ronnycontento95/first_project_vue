<script setup>
import { computed, ref } from "vue";
import LoadingSpinner from "./components/LoadingSpinner.vue";
import BlogPost from "./components/BlogPost.vue";
import PaginatePostVue from "./components/PaginatePost.vue";

const postsData = ref([]);

const favoritoref = ref("");
const postPage = 10;
const inicio = ref(0);
const fin = ref(10);
const loading = ref(true);

const next = () => {
  inicio.value = inicio.value + postPage;
  fin.value = fin.value + postPage;
};

const previus = () => {
  inicio.value += -postPage;
  fin.value += -postPage;
};
const fijarFavorito = (title) => {
  favoritoref.value = title;
};
fetch("https://jsonplaceholder.typicode.com/posts")
  .then((res) => res.json())
  .then((data) => {
    postsData.value = data;
  }).finally(()=> {
    setTimeout(() => {
      loading.value = false
    }, 2000);
  });

const maxlenght = computed(() =>postsData.value.length)
</script>

<template>
  <LoadingSpinner v-if="loading"/>
  <div class="container" v-else>
    <h1>APP RONNY</h1>
    <h2>MI FAVORTITE IS {{ favoritoref }}</h2>
    <PaginatePostVue
      @previus="previus"
      @next="next"
      :inicio="inicio"
      :fin="fin"
      :maxlenght="maxlenght"
      class="mb-2"
    />
    <BlogPost
      v-for="post in postsData.slice(inicio, fin)"
      :key="post.title"
      :title="post.title"
      :id="post.id"
      :body="post.body"
      class="mb-2"
      :fijarFavorito="fijarFavorito"
    />
  </div>
</template>
