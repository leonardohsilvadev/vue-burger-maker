<template>
  <div class="message-container">
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  name: 'Message',
  props: {
    message: String,
  }
}
</script>

<style scoped>
  .message-container {
    color: #004085;
    background-color: #CCE5FF;
    border: 0.125rem solid #B8DAFF;
    border-radius: 0.313rem;
    padding: 0.625rem;
    max-width: 25rem;
    margin: 1.875rem auto;
 }
</style>