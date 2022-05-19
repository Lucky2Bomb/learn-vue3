<template>
  <div class="post p-2">
    
    <div class="post__title">
      <h4>{{ post.title }}</h4>
    </div>
    
    <div class="post__body ps-1 ps-1">{{ post.body }}</div>
    
    <div class="d-flex justify-content-end">
      <delete-button
      @click="$emit('remove', post)"
      >Delete</delete-button>
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
  border: 1px solid #aaaaaa;
  margin-top: 8px;
}

.post__body {
  font-style: italic;
}
</style>