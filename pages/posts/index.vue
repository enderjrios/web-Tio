<template>
  <div>
    <H1>Posts</H1>
    <Posts
      v-for="post of posts"
      :key="post.id"
      :id="post.id"
      :name="post.title"
      :content="post.body"
    />
  </div>
</template>

<script>
import axios from "axios";
import Posts from "../../components/Posts";
export default {
  components: {
    Posts,
  },
  data() {
    return {
      posts: [],
    };
  },
  async created() {
    const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
    this.posts = res.data;
  },
};
</script>