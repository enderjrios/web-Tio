<template>
  <div class="container">
    <div class="card">
    <h2>titulo: {{post.title}}</h2>
    <p>Id: {{post.id}}</p>
    <p>Contenido: {{post.body}}</p>
  </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  head() {
    return {
      title: `Editing Post ${this.$route.params.id}`,
    };
  },
  data() {
    return {
      post: {},
    };
  },
  async created() {
    const res = await axios.get("https://jsonplaceholder.typicode.com/posts/" + this.$route.params.id);
    this.post = res.data;
    console.log(this.$route.params.id);
  },
};
</script>

<style>
.card {
  border: 1px solid rgb(51, 4, 126);
  padding: 4rem;
  background: #3e3e3e;
  color: white;
}
</style>