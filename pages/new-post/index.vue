<template>
  <section class="new-post">
    <div class="container">
      <form @submit.prevent="createPost">
        <div class="form-group">
          <label for="">Movie title</label>
          <input
            required
            type=""
            id=""
            class="form-control"
            name=""
            v-model="newMovie.title"
          />
        </div>
        <div class="form-group">
          <label for="">Movie Image</label>
          <input
            required
            type=""
            id=""
            class="form-control"
            name=""
            v-model="newMovie.image"
            placeholder="Enter a valid image link to display your awesome movie"
          />
        </div>
        <div class="form-group">
          <label for="">Release Date</label>
          <input
            required
            type="date"
            id=""
            class="form-control"
            name=""
            v-model="date"
          />
        </div>
        <div class="form-group">
          <label for="">Movie Preview</label>
          <input
            required
            type="text"
            id=""
            class="form-control"
            name=""
            v-model="newMovie.preview"
          />
        </div>
        <div class="form-group">
          <label for="">Movie synopsis </label>
          <textarea
            type=""
            id=""
            class="form-control"
            name=""
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
import slugify from 'slugify'
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
    createPost() {
      this.$axios
        .$post('https://movie-library-7e5ec.firebaseio.com/posts.json', {
          ...this.newMovie,
          date: moment(this.date).format('MMM Do YYYY'),
          id: slugify(this.newMovie.title, {
            replacement: '-', // replace spaces with replacement character, defaults to `-`
            remove: /[*+~.()'"!:@]/g, // remove characters that match regex, defaults to `undefined`
            lower: true, // convert to lower case, defaults to `false`
            strict: true, // strip special characters except replacement, defaults to `false`
          }),
        })
        .then((res) => {
          console.log(res)
        })
        .catch((e) => {
          console.log(e)
        })
    },
  },
}
</script>

<style>
</style>