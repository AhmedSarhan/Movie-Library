<template>
  <section class="header-component">
    <div class="container-fluid">
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <nuxt-link class="navbar-brand" to="/">Awesome Movie Library</nuxt-link>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav ml-auto">
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/"
                >Home <span class="sr-only">(current)</span></nuxt-link
              >
            </li>
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/about/">About</nuxt-link>
            </li>
            <li class="nav-item">
              <nuxt-link class="btn btn-success" to="/new-post"
                >Create Post</nuxt-link
              >
            </li>
          </ul>
        </div>
      </nav>
    </div>
  </section>
</template>

<script>
export default {}
</script>

<style scoped>
.nav-item .btn-success {
  font-size: 20px;
  margin-top: 10px;
}
.nav-item {
  margin-left: 10px;
  margin-right: 10px;
}
.nav-link {
  margin-top: 10px;
  font-size: 20px;
  font-weight: 600;
}
.nav-link.nuxt-link-exact-active {
  color: #3f51b5 !important;
  border-bottom: 2px solid #3f51b5;
}
@media only screen and (max-width: 991px) {
  .nav-item {
    margin-left: 0;
    margin-bottom: 10px;
  }
}
</style>