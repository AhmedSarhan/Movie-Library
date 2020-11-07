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
  mounted() {
    this.$axios
      .$get('https://movie-library-7e5ec.firebaseio.com/posts.json')
      .then((response) => {
        this.loadedPosts = Object.values(response)
        console.log(this.loadedPosts)
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
    //
    //
  },
  computed: {},
  components: {
    PostsPreview,
  },

  methods: {
    // pushPosts() {
    //   for (let i = 0; i <= this.loadedPosts.length; i++) {
    //     this.$axios
    //       .$post(
    //         'https://movie-library-7e5ec.firebaseio.com/posts.json',
    //         this.loadedPosts[i]
    //       )
    //       .then((res) => {
    //         console.log(res)
    //       })
    //   }
    // },
  },
}
</script>

<style>
</style>
