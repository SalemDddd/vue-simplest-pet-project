<template>
  <form action="" @submit.prevent>
    <h3 class="creator">Создание поста</h3>
    <MyInput v-model="post.title" placeholder="Название" />
    <MyInput v-model="post.body" placeholder="Описание" />
    <MyButton class="btn btn-create" @click="createPost"> Создать </MyButton>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost(e) {
      let id = Date.now();
      this.$emit("create", { id, ...this.post });
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style>
form {
  max-width: 250px;
  margin: auto;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.btn-create {
  align-self: flex-end;
}
</style>
