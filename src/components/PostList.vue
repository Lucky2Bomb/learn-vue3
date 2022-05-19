<template>
  <div class="post-list" v-show="posts.length > 0">
    <h2>Posts:</h2>
    <post-item class="post" v-for="post in posts" :key="post.id" :post="post" @remove="$emit('remove', post)" />
  </div>
</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.post-list {
  padding: 8px;
}
</style>
