<template>
  <div class="app">
    <router-view></router-view>
  </div>
</template>
<script>
export default {};
</script>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.mt-15 {
  margin-top: 15px;
}

.app {
  padding: 20px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
.app__btns {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.container > h1 {
  font-weight: 900;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
.container {
  max-width: 800px;
  margin: auto;
}
.page__wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 7px;
}
</style>
