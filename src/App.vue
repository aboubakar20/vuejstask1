<template>
  <div id="app">
    <h1>Test app</h1>
    <button @click="fetchDatafromAPI()">Go</button>
    <p>{{ info }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      info: null,
    };
  },
  methods: {
    fetchDatafromAPI() {
      axios
        .get("https://api.coindesk.com/v1/bpi/currentprice.json")
        .then((response) => (this.info = response));
    },
  },
};
</script>

<style>
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
