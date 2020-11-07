<template>
  <section id="about-page">
    <div class="container">
      <h3 class="text-center">
        Hi, that's a nuxtjs simple blog with some Bootstrap and Firebase~axios
        api
      </h3>
      <h5 class="text-center">
        check more of my works at
        <a href="https://sarahan-portfolio.netlify.app/" target="_blank"
          >My Portfolio</a
        >
      </h5>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      info: null,
    }
  },
}
</script>

<style scoped>
h3 {
  padding-top: 150px;
}
h5 {
  margin-top: 20px;
  font-size: 18px;
  color: #979797;
}
</style>