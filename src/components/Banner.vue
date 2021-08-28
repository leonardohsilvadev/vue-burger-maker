<template>
  <div id="banner">
    <h1>Make your burger</h1>
  </div>
</template>

<script>
export default {
  name: 'Banner'
}
</script>

<style scoped>
  #banner {
    background-image: url('/img/burger.jpg');
    background-position: 0;
    background-size: cover;
    height: 20rem;
    display: flex;
    justify-content: flex-start;
    align-items: center;
  }

  #banner h1 {
    color: #fff;
    text-align: center;
    font-size: 6rem;
    /* background-color: #222; */
    padding-left: 20rem;
  }
</style>