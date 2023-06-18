<template>
  <div class="page__wrapper">
    <div v-for="pageNum in pages" :key="pageNum">
      <MyButton
        :class="{
          'page-active': pageNum === page,
        }"
        @click="changePage(pageNum)"
      >
        {{ pageNum }}
      </MyButton>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    pages: {
      type: Number,
    },
    page: {
      type: Number,
    },
  },
  methods: {
    changePage(pageNum) {
      this.$emit("update", pageNum);
    },
  },
};
</script>
<style>
.page-active {
  background: teal !important;
  color: white !important;
}
</style>
