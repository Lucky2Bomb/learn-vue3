<template>
  <input
    :value="value"
    @input="updateInput"
    type="text"
    class="form-control"
  />
</template>

<script>
export default {
  name: "top-input",
  props: {
    value: [String, Number],
  },
  methods: {
    updateInput(event) {
      this.$emit("update:value", event.target.value);
    },
  },
};
</script>

<style scoped>
</style>