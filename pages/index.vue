<template>
  <div class="container">
    <h1 class="text-center">Movie Library</h1>
    <PostsPreview :posts="loadedPosts" />
  </div>
</template>

<script>
import PostsPreview from '@/components/Blog/PostsPreview'
export default {
  data() {
    return {
      loadedPosts: [],
    }
  },
  async fetch() {
    await this.$axios
      .$get('https://movie-library-7e5ec.firebaseio.com/posts.json')
      .then((response) => {
        this.loadedPosts = Object.values(response)
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
  components: {
    PostsPreview,
  },
}
</script>

<style>
</style>
