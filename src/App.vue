<template>
  <div id="app">
    <h1>Test app</h1>
    <button @click="getPosts()">Go</button>
    <PostsTable
      v-bind:posts="posts"
      v-on:postData="getAndShowPostDetail"
    ></PostsTable>
    <DetailCard v-bind:postDetails="cardDetails" v-if="isShow"></DetailCard>
  </div>
</template>

<script>
import axios from "axios";
import PostsTable from "./components/PostsTable";
import DetailCard from "./components/DetailCard";
export default {
  name: "App",
  components: {
    PostsTable,
    DetailCard,
  },
  data() {
    return {
      posts: null,
      cardDetails: null,
      isShow: false,
    };
  },
  methods: {
    async getPosts() {
      const response = await axios.get(
        "https://www.reddit.com/r/technology/new.json"
      );
      this.posts = response.data.data.children;
    },

    getAndShowPostDetail(postDetail) {
      this.cardDetails = postDetail;
      this.isShow = true;
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
  margin: 10px;
}
</style>
