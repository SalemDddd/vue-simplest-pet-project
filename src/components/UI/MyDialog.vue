<template>
  <div
    class="dialog"
    v-if="show"
    @click.stop="this.$emit('update:show', false)"
  >
    <div class="dialog__content" @click.stop><slot></slot></div>
  </div>
</template>
<script>
export default {
  name: "MyDialog",
  props: {
    show: {
      type: Boolean,
      defualt: false,
    },
  },
};
</script>
<style>
.dialog {
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  display: flex;
}
.dialog__content {
  margin: auto;
  padding-top: 15px;
  background: white;
  border-radius: 12px;
  min-height: 50px;
  min-width: 300px;
}
</style>
