<template>
  <select class="form-select" v-model="modelValue">
    <option disabled selected value="">Open this select menu</option>
    <option v-for="option in options" :key="option.id" :value="option.value">{{ option.name }}</option>
  </select>
</template>

<script>
export default {
  name: "select-list",
  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    changeOption(e) {
      this.$emit('update:modelValue', e.target.value);
    }
  }
};
</script>

<style scoped>
</style>