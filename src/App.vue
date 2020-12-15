<template>
  <div id="app">
    <h1>Test app</h1>
    <button @click="getPosts()">Go</button>
    <PostsTable v-bind:posts="posts"></PostsTable>
  </div>
</template>

<script>
import axios from "axios";
import PostsTable from "./components/PostsTable";
export default {
  name: "App",
  components: {
    PostsTable,
  },
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    async getPosts() {
      try {
        const response = await axios.get(
          "https://www.reddit.com/r/technology/new.json"
        );
        this.posts = response.data.data.children;
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  font-size: 20px;
  padding: 5px 20px;
}
</style>
