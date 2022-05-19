<template>
  <div class="container mt-2">
    <div class="d-flex justify-content-between">
      <modal>
        <template v-slot:trigger>
          <create-button>create post</create-button>
        </template>
        <post-form @create="createPost" />
      </modal>
      <div><select-list v-model="selectedSort" :options="sortOptions" /></div>
    </div>
    <hr />
    <loading v-if="isLoading" />
    <post-list :posts="posts.reverse()" @remove="removePost" />
  </div>
</template>
<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import axios from "axios";

export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [],
      isLoading: false,
      selectedSort: '',
      sortOptions: [
        { value: "title", name: "По названию" },
        { value: "body", name: "По содержимому" },
      ],
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    async artificialFetchPosts() {
      this.isLoading = true;
      setTimeout(() => this.fetchPosts(), 2000);
    },
    async fetchPosts() {
      this.isLoading = true;
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts",
          { params: { _limit: 10, offset: 10 } }
        );
        this.posts = response.data;
      } catch (error) {
        alert(error);
      } finally {
        this.isLoading = false;
      }
    },
  },
  mounted() {
    this.artificialFetchPosts();
  },
  watch: {
    selectedSort: function (newValue) {
      console.log(newValue);
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
