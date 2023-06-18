<template>
  <div class="post">
    <div>
      <div><strong>Номер поста:</strong> {{ post.id }}</div>
      <div><strong>Название:</strong> {{ post.title }}</div>
      <div><strong>Описание:</strong> {{ post.body }}</div>
    </div>
    <div class="post__btns">
      <MyButton @click="$emit('remove', post)"> Удалить </MyButton>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>
<style scoped>
.post {
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border: 2px solid teal;
  padding: 10px 30px;
  border-radius: 15px;
}
.post:hover {
  background: rgb(245, 245, 245);
}
</style>
