<template>
  <select class="form-select" v-model="modelValue" @select="changeOption">
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
    changeOption(event) {
      console.log(event.target.value);
      this.$emit('update:modelValue', event.target.value);
    }
  }
};
</script>

<style scoped>
</style>