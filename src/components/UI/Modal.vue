<template>
  
  <!-- Button trigger modal -->
  <div
    data-bs-toggle="modal"
    data-bs-target="#modal_form"
  >
    <slot name="trigger"></slot>
  </div>

  <!-- Modal -->
  <div
    class="modal fade"
    id="modal_form"
    tabindex="-1"
    aria-labelledby="modal_formLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div v-if="enableHeader" class="modal-header">
          <slot name="header"></slot>
        </div>
        <div class="modal-body">
          <slot></slot>
        </div>
        <div v-if="enableFooter" class="modal-footer">
          <slot name="footer"></slot>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "modal",
  props: {
    show: {
      type: Boolean,
      default: false,
    },
    enableHeader: {
      type: Boolean,
      default: false,
    },
    enableFooter: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped>
</style>