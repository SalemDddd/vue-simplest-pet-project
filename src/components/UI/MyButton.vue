<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>
<script>
export default {
  name: "MyButton",
};
</script>
<style>
.btn {
  margin: 15px 0;
  padding: 10px 15px;
  background: none;
  color: teal;
  cursor: pointer;
  border: 1px solid teal;
  font-family: Arial, Helvetica, sans-serif;
}
.btn:hover {
  background: teal;
  color: white;
}
</style>
