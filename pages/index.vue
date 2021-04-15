<template>
  <div class="container">
    <h1 class="text-center">Movie Library</h1>
    <PostsPreview :posts="loadedPosts" />
  </div>
</template>

<script>
import axios from 'axios'
import PostsPreview from '@/components/Blog/PostsPreview'
export default {
  data() {
    return {
      loadedPosts: [],
    }
  },
  async fetch() {
    await axios
      .get('https://movie-library-7e5ec.firebaseio.com/posts.json')
      .then((res) => {
        if (!res.data) {
          return
        }
        console.log(res.data)
        console.log(typeof res.data)

        let moviesArr = []
        for (let key in res.data) {
          moviesArr.push({ ...res.data[key], id: key })
        }
        console.log(moviesArr)
        this.loadedPosts = [...moviesArr]
      })
      .catch((err) => {
        console.log(err)
      })
  },
  components: {
    PostsPreview,
  },
}
</script>

<style>
</style>
