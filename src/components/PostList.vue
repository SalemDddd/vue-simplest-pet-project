<template>
  <div class="mt-15" v-if="posts.length">
    <h3>Список постов</h3>
    <TransitionGroup name="post-list">
      <PostItem
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
      />
    </TransitionGroup>
  </div>
  <h2 v-else class="none-posts mt-15">Список постов пуст</h2>
</template>

<script>
import PostItem from "./PostItem.vue";
export default {
  components: {
    PostItem,
  },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
.none-posts {
  color: red;
  text-align: center;
  font-weight: 900;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
.post-list-enter-active,
.post-list-move,
.post-list-leave-active {
  transition: all 1s ease;
}
.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>
