<template>
  <select class="select" v-model="modelValue" @change="changeOption">
    <option disabled>Выберите из списка</option>
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>
<script>
export default {
  name: "MySelect",
  props: {
    sort: {
      type: String,
    },
    options: {
      type: Array,
      defualt: () => [],
    },
  },
  methods: {
    changeOption(event) {
      this.$emit("update:changeOption", event.target.value);
    },
  },
};
</script>
<style scoped>
.select {
  border: 1px solid black;
  max-height: 30px;
  background: white;
  padding-left: 5px;
}
</style>
