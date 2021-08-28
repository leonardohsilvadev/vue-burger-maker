<template>
  <footer class="footer">
  <p>Make Your Burger &copy; 2021</p>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>
  .footer {
    height: 12.5rem;
    background-color: #222;
    border-top: 0.25rem solid #111;
    color: #FCBA03;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    position: absolute;
    bottom: 0;
  }
</style>