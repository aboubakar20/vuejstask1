<template>
  <div>
    <section>
      <article class="card">
        <h3>Author:</h3>
        <p
          v-for="postDetails in postDetail"
          :key="'author' + postDetails.id + '191'"
        >
          {{ postDetails.author }}
        </p>
        <h3>Title:</h3>
        <p v-for="postDetails in postDetail" :key="'title' + postDetails.id">
          {{ postDetails.title }}
        </p>
      </article>
    </section>
  </div>
</template>

<script>
export default {
  props: ["postDetail"],
};
</script>

<style scoped>
section {
  display: grid;
  width: 100%;
  flex-wrap: wrap;
  justify-content: center;
}

.card {
  border: 1px solid black;
  margin: 5px;
  padding: 5px 25px 5px 25px;
  display: grid;
  justify-content: left;
  width: 25em;
  box-shadow: -3px 3px 3px rgba(0, 0, 0, 0.5), 0 1px 2px rgba(0, 0, 0, 0.24);
}
h3,
p {
  margin: 10px;
}
</style>
