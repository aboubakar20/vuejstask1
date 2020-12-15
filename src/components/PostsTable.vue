<template>
  <div>
    <table>
      <thead>
        <tr>
          <th>Sr#</th>
          <th>Author</th>
          <th>Title</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(post, index) in posts"
          :key="'post-row-' + post.data.created"
        >
          <td>{{ index + 1 }}</td>
          <td>{{ post.data.author_fullname }}</td>
          <td>{{ post.data.title }}</td>
          <td><button>Detail</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "PostsTable",
  props: ["posts"],
};
</script>

<style scoped>
button {
  font-size: 20px;
  padding: 5px 20px;
  background: #3498db;
  color: #eee;
}
table {
  width: 750px;
  border-collapse: collapse;
  margin: 50px auto;
}
tr:nth-of-type(odd) {
  background: #eee;
}
th {
  background: #3498db;
  color: white;
  font-weight: bold;
}
td,
th {
  padding: 10px;
  border: 1px solid #ccc;
  text-align: left;
  font-size: 18px;
}
@media only screen and (max-width: 760px),
  (min-device-width: 768px) and (max-device-width: 1024px) {
  table {
    width: 100%;
  }
  table,
  thead,
  tbody,
  th,
  td,
  tr {
    display: block;
  }
  thead tr {
    position: absolute;
    top: -9999px;
    left: -9999px;
  }

  tr {
    border: 1px solid #ccc;
  }

  td {
    border: none;
    border-bottom: 1px solid #eee;
    position: relative;
    padding-left: 50%;
  }

  td:before {
    position: absolute;
    top: 6px;
    left: 6px;
    width: 45%;
    padding-right: 10px;
    white-space: nowrap;
    content: attr(data-column);

    color: #000;
    font-weight: bold;
  }
}
</style>
