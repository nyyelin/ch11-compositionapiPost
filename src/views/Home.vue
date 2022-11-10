<template>
  <div class="home">
    <div v-if="posts.length > 0">
      <PostList :posts="posts"> </PostList>
    </div>
    <div v-else>
      <Spinner></Spinner>
    </div>
    <div v-if="error">
      {{ error }}
    </div>
  </div>
</template>

<script>
import Spinner from "../components/Spinner";
import PostList from "../components/PostList.vue";
import getPosts from "../composable/getPosts.js";
// @ is an alias to /src

export default {
  components: {
    Spinner,
    PostList,
  },
  setup() {
    let { posts, error, load } = getPosts();
    load();
    return { posts, error };
  },
};
</script>

<style>
.home {
  max-width: 1200px;
  margin: 0 auto;
  padding: 10px;
}
</style>
