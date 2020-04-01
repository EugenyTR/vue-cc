<template>
  <div id="app">
    <PostsForm />
    <h1>{{postsCount}}</h1>
    <div class='posts' v-for="post in validPosts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex';
import PostsForm from './components/PostsForm';
export default {
  name: 'App',
  computed: mapGetters(["validPosts", "postsCount"]),
  methods: mapActions(["fetchPosts"]),
  components: { PostsForm },
  async mounted() {
    this.fetchPosts();
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}

.posts {
  border: 1px sold #ccc;
  border-radius: 4px;
  margin-bottom: 1rem;
}
</style>
