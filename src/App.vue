<template>
  <Navbar :logo="logo" :alt="appName" />
  <router-view/>
  <Footer />
</template>

<script>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

export default {
  components: {
    Navbar,
    Footer
  },
  data() {
    return {
      logo: '/img/logo.png',
      appName: 'Make Your Burger'
    }
  }
}
</script>

<style>
  * {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  .container {
    margin: 3.125rem;
    min-width: 15.625rem;
  }

  h1 {
    text-align: center;
    font-size: 2.625rem;
    margin-bottom: 1.875rem;
    color: #222;
  }
</style>
