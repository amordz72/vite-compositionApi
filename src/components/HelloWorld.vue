<script   >
import axios from "axios";
import { onMounted, reactive, ref } from "vue";
export default {
  setup() {
    const state = reactive({
      title: "test_t",
      posts: [],
    });

    const get_posts = async function () {
      await axios.get(
        "https://jsonplaceholder.typicode.com/posts"
      ).then((obj) => {
        state.posts = obj.data
      });
    };

    onMounted(() => {
      get_posts();
    });

    return {
      state
    };
  },
};
</script>
<template>
  <div>
    <h1>{{ title }}</h1>
    <ul>
      <li v-for="p in state.posts" :key="p.id">{{ p.title }}</li>
    </ul>
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
