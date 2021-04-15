<template>
  <div class="posts-preview">
    <div class="row" v-if="posts && posts.length">
      <div class="col-md-4" v-for="post in posts" :key="post.id">
        <div class="card">
          <img class="card-img-top" :src="post.image" alt="Meal 1" />
          <div class="card-body">
            <h5 class="card-title">{{ post.title }}</h5>
            <h6 class="card-subtitle mb-2 text-muted">
              Released at: {{ post.date }}
            </h6>
            <p class="card-text">{{ post.preview }}</p>
            <nuxt-link :to="post.id" class="card-link"
              >ReadMore <i class="fa fa-arrow-right" aria-hidden="true"></i
            ></nuxt-link>
          </div>
        </div>
      </div>
    </div>
    <div v-else>
      <h3 class="text-center my-4">No movies added yet</h3>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
}
</script>

<style scoped>
.card {
  margin-top: 10px;
  margin-bottom: 10px;
}
.card-subtitle {
  color: #ccc !important;
  font-size: 16px !important;
}
</style>