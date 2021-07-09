<template>
  <div id="app">
    <PostForm />
    <h1>{{postsCount}}</h1>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex';
import PostForm from './components/PostForm.vue';
export default {
  name: 'App',
  computed: mapGetters(['validPosts', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  async mounted() {
    this.fetchPosts(4);
  },
  components: { PostForm }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 400px;
}

.post {
  border: 1px solid #cccccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}
</style>
