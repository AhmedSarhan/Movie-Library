<template>
  <section class="single-post-page">
    <div class="container">
      <div
        class="post-thumbnail"
        :style="{
          backgroundImage: 'url(' + post.image + ')',
          marginBottom: '20px',
        }"
      ></div>
      <article class="article-content">
        <h3 class="article title">{{ post.title }}</h3>
        <h5 class="article-date">Released at: {{ post.date }}</h5>
        <p class="article-content">{{ post.content }}</p>
      </article>
    </div>
  </section>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      postId: this.$route.params.postId,
      post: {},
    }
  },
  async fetch() {
    await axios
      .get(
        `https://movie-library-7e5ec.firebaseio.com/posts/${this.postId}.json`
      )
      .then((res) => {
        this.post = { ...res.data }
      })
      .catch((err) => {
        console.log(err)
      })
  },
  computed: {},
  mounted() {},
}
</script>

<style scoped>
.post-thumbnail {
  height: 400px;
  width: 100%;
  background-size: contain;
  background-repeat: no-repeat;
}
</style>