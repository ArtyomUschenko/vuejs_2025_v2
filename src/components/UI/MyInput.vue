<template>
  <input :value="modelValue" @input="updateInput" class="input" type="text">
</template>

<script>
  export default {
    name: "MyInput",
    props: {
      modelValue: [String, Number],
    },
    methods: {
      updateInput(event) {
        this.$emit('update:modelValue', event.target.value)
      }
    }
  }
</script>

<style scoped>
.input {
  margin-top: 10px;
  display: block;
  width: 50%;
  padding: 10px;
  border: 3px solid #ccc;
  border-radius: 5px;
  font-size: 20px;
}
</style>