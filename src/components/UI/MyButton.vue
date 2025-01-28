<template>
  <button class="btn">
      <slot></slot>
  </button>
</template>



<script>
  export default {
    name: "my-button",
  }
</script>



<style scoped>
.btn {
  padding: 10px;
  border: 3px solid #ccc;
  border-radius: 5px;
  font-size: 20px;
  background-color: #ccc;
  color: #fff;
  cursor: pointer;
}
</style>