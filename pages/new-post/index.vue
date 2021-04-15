<template>
  <section class="new-post">
    <div class="container">
      <form @submit.prevent="createPost">
        <div class="form-group">
          <label for="">Movie title</label>
          <input
            required
            type="text"
            id="title"
            class="form-control"
            name="title"
            v-model="newMovie.title"
          />
        </div>
        <div class="form-group">
          <label for="">Movie Image</label>
          <input
            required
            type="url"
            id="image"
            class="form-control"
            name="image"
            v-model="newMovie.image"
            placeholder="Enter a valid image link to display your awesome movie"
          />
        </div>
        <div class="form-group">
          <label for="">Release Date</label>
          <input
            required
            type="date"
            id="date"
            class="form-control"
            name="date"
            v-model="date"
          />
        </div>
        <div class="form-group">
          <label for="">Movie Preview</label>
          <input
            required
            type="text"
            id="preview"
            class="form-control"
            name="preview"
            v-model="newMovie.preview"
          />
        </div>
        <div class="form-group">
          <label for="">Movie synopsis </label>
          <textarea
            id="synopsis"
            class="form-control"
            name="synopsis"
            v-model="newMovie.content"
            rows="3"
            required
          ></textarea>
        </div>
        <input
          required
          class="btn btn-primary"
          type="submit"
          value="Add Movie"
        />
      </form>
    </div>
  </section>
</template>

<script>
import moment from 'moment'
import axios from 'axios'
export default {
  data() {
    return {
      date: '',
      newMovie: {
        title: '',
        image: '',
        preview: '',
        content: '',
      },
    }
  },
  mounted() {},
  methods: {
    async createPost() {
      await axios
        .post('https://movie-library-7e5ec.firebaseio.com/posts.json', {
          ...this.newMovie,
          date: moment(this.date).format('MMM Do YYYY'),
        })
        .then((res) => {
          this.$router.push('/')
        })
    },
  },
}
</script>

<style>
</style>