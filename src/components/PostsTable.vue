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
import "../../node_modules/ag-grid-community/dist/styles/ag-grid.css";
import "../../node_modules/ag-grid-community/dist/styles/ag-theme-alpine.css";
import DetailButton from "./DetailButton.vue";

export default {
  name: "PostsTable",
  components: {
    AgGridVue,
  },
  data() {
    return {
      columnDefs: this.columnDef(),
      rowData: null,
      frameworkComponents: null,
    };
  },
  props: ["posts"],
  methods: {
    onGridReady() {},
    columnDef: function() {
      return [
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
          cellRenderer: "detailBtnCellRenderer",
          cellRendererParams: {
            clicked: function(key) {
              alert(`${key} was clicked`);
            },
          },
        },
      ];
    },
  },
  beforeMount() {
    this.rowData = this.posts;
    this.frameworkComponents = {
      detailBtnCellRenderer: DetailButton,
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
