<template>
  <section class="single-post-page">
    <div class="container" v-for="post in posts" :key="post.id">
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
export default {
  data() {
    return {
      postId: this.$route.params.postId,
      posts: [],
      newPosts: [],
    }
  },
  async fetch() {
    await this.$axios
      .$get('https://movie-library-7e5ec.firebaseio.com/posts.json')
      .then((res) => {
        let loadedPosts = {}
        loadedPosts = { ...res }
        this.posts = Object.values(loadedPosts).filter(
          (post) => post.id === this.postId
        )
      })
      .catch((res) => {
        if (!res.response) {
          console.error(res)
          context.error({
            statusCode: 404,
            message: 'Failed to receive content form api',
          })
        } else {
          console.error(res.response.data)
          context.error({
            statusCode: res.response.status,
            message: res.response.data,
          })
        }
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