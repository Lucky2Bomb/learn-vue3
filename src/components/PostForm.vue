<template>
  <form class="p-2" @submit.prevent>
    <h3>Create post</h3>

    <div>
      <label for="title" class="form-label">title</label>
      <top-input v-model:value="post.title" placeholder="title" />
    </div>

    <div>
      <label for="body" class="form-label">body</label>
      <top-input v-model:value="post.body" placeholder="body" />
    </div>

    <div class="d-flex justify-content-end mt-3">
      <create-button @click="createPost" :disabled="!post.title || !post.body"
        >Send</create-button
      >
    </div>
  </form>
</template>

<script>
export default {
  name: "post-form",
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
  watch: {
    post: {
      handler(newVal) {
        console.log(newVal);
      },
      deep: true,
    },
  },
};
</script>

<style scoped>
</style>
