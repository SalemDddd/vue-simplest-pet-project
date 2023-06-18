<template>
  <div class="center">
    <h1>Welcome Vue 3</h1>
    <router-link to="/posts">Перейти к постам</router-link>
  </div>
</template>
<script>
export default {};
</script>
<style scoped>
.center > a {
  text-decoration: none;
}
.center > a:hover {
  text-decoration: underline;
}
.center {
  max-width: 400px;
  margin: auto;
  text-align: center;
}
</style>
