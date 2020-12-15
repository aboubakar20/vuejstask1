<template>
  <div id="app">
    <h1>Test app</h1>
    <button @click="getPosts()">Go</button>
    <p>{{ posts }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      posts: null,
    };
  },
  methods: {
    async getPosts() {
      // try {
      const response = await axios.get(
        "https://www.reddit.com/r/technology/new.json"
      );
      return (this.posts = await response.data.data.children);
      // } catch (error) {
      //   alert(error);
      // }
    },

    // getPosts() {
    //   axios
    //     .get("https://www.reddit.com/r/technology/new.json")
    //     .then((response) => (this.books = response.data.data.children));
    // },
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
