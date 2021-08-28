<template>
  <Banner />
  <div class="container">
    <h1>Build your burger</h1>
    <BurgerForm />
  </div>
</template>

<script>
import Banner from '../components/Banner.vue'
import BurgerForm from '../components/BurgerForm.vue'

export default {
  name: 'Home',
  components: {
    Banner,
    BurgerForm
  }
}
</script>
