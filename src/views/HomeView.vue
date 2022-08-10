<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
    };
  },
  created: function () {
    this.getPostsData();
  },
  methods: {
    getPostsData: function () {
      axios.get("https://jsonplaceholder.typicode.com/posts").then((response) => {
        console.log(response.data);
        this.posts = response.data;
      });
    },
    getNewsData: function () {
      axios.get("/newsapi_headlines").then((response) => {
        console.log("news api", response.data);
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="post in posts" v-bind:key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<style></style>
