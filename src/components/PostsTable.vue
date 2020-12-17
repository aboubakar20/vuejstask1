<template>
  <ag-grid-vue
    class="ag-theme-alpine"
    :columnDefs="columnDefs"
    :rowData="posts"
    :frameworkComponents="frameworkComponents"
    @grid-ready="onGridReady"
  >
  </ag-grid-vue>
</template>

<script>
import { AgGridVue } from "ag-grid-vue";
import BtnCellRenderer from "./btn-cell-renderer.vue";

export default {
  name: "PostsTable",
  components: {
    AgGridVue,
  },
  data() {
    return {
      columnDefs: null,
      rowData: null,
      frameworkComponents: null,
    };
  },
  props: ["posts"],
  methods: {
    onGridReady(params) {
      this.gridApi = params.api;
      this.columnApi = params.columnApi;
    },
  },
  beforeMount() {
    this.rowData = this.posts;
    this.columnDefs = [
      {
        headerName: "Author",
        field: "data.author",
        sortable: true,
        filter: true,
      },
      {
        headerName: "Title",
        field: "data.title",
        sortable: true,
        filter: true,
      },
      {
        headerName: "Action",
        field: "data.created",
        cellRenderer: "btnCellRenderer",
        cellRendererParams: {
          clicked: function(key) {
            alert(`${key} was clicked`);
          },
        },
      },
    ];
    this.frameworkComponents = {
      btnCellRenderer: BtnCellRenderer,
    };
  },
};
</script>
<style scoped>
button {
  font-size: 20px;
  padding: 5px 20px;
  background: #3498db;
  color: #eee;
}
.ag-theme-alpine {
  width: 700px;
  height: 300px;
  margin: 0 auto;
}
</style>
