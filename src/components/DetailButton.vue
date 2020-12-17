<template>
  <div>
    <span>
      <button @click="btnClickedHandler()">Detail</button>
    </span>
  </div>
</template>

<script>
import Vue from "vue";
export default Vue.extend({
  methods: {
    btnClickedHandler() {
      this.params.clicked(this.params.value);
    },
  },
});
</script>
<style scoped>
button {
  font-size: 20px;
  padding: 5px 20px;
}
</style>
