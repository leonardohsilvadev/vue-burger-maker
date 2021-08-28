<template>
  <div id="nav">
    <router-link to="/">
      <img :src="logo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Home</router-link>
    <router-link to="/orders">Orders</router-link>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  props: ['logo', 'alt']
}
</script>

<style scoped>
 #nav {
   background-color: #222;
   border-bottom: 0.25rem solid #111;
   padding: 0.938rem;
   display: flex;
   align-items: center;
 }

 #nav a {
   color: #FCBA03;
   text-decoration: none;
   margin: 0.75rem;
   transition: 0.5s;
 }

 #nav a:hover {
   color: #FFF;
 }

 #logo {
   width: 2.5rem;
   height: 2.5rem;
 }
</style>