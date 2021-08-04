<template>
  <div>
    <Header />
    <main>
      <Slider/>
      <Main/>
      <Form/>
      <Footer/>
      <Bottom/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Slider from './components/Slider.vue'
import Main from './components/Main.vue'
import Form from './components/Form.vue'
import Footer from './components/Footer.vue'
import Bottom from './components/Bottom.vue'

export default {
  name: 'App',
  components: {
    Header, Slider, Main, Form, Footer, Bottom,
  }
}
</script>

<style lang="scss">
  @import "~@/assets/scss/vendors/bootstrap-vue/index";
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&display=swap');

  #app, body {
    font-family: "Montserrat", Helvetica, Arial, sans-serif;
  }

  body {
    min-width: 1200px;

    @include respond-to(sm) {
      min-width: auto;
    }
  }

  .container-lg, .container-md, .container-sm, .container {
    min-width: 1200px;

    @include respond-to(sm) {
      min-width: auto;
    }
  }

  a {
    &:hover {
      text-decoration: none;
    }
  }

</style>
