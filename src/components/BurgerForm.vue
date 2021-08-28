<template>
  <div>
    <form id="form">
       <div class="input-container">
         <label for="name">Name</label>
         <input type="text" name="name" v-model="name" placeholder="enter your name" />
       </div>

        <div class="input-container">
         <label for="bread">Choose the bread</label>
         <select name="bread" v-model="bread">
         </select>
       </div>

        <div class="input-container">
         <label for="meat">Choose the meat</label>
         <select name="meat" v-model="meat">
         </select>
       </div>

       <div id="optionals-container" class="input-container">
         <label id="optionals-title" for="optionals">Choose the optionals</label>
         <div class="checkbox-container">
           <input type="checkbox" name="optionals" v-model="optionals" value="mayo" />
           <span>mayo</span>
         </div>

         <div class="input-container">
           <input type="submit" class="submit" value="place order">
         </div>
       </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'BurgerForm'
}
</script>

<style scoped>
  #form {
    max-width: 25rem;
    margin: 0 auto;
  }

  .input-container {
    display: flex;
    flex-direction: column;
    margin-bottom: 1.25rem;
  }

  label {
    font-weight: bold;
    margin-bottom: 0.875rem;
    color: #222;
    padding: 0.313rem 0.625rem;
    border-left: 0.25rem solid #FCBA03;
  }

  input, select {
    padding: 1rem;
    width: 18.75rem;
  }

  #optionals-container {
    flex-direction: row;
    flex-wrap: wrap;
  }

  #optionals-title {
    width: 100%;
  }

  .checkbox-container {
    display: flex;
    align-items: center;
    width: 50%;
    margin-bottom: 1.25rem;
    cursor: pointer;
  }

  .checkbox-container span, input {
    width: auto;
  }

  .checkbox-container span {
    margin-left: 0.375rem;
    font-weight: bold;
  }

  .submit {
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    border: 0.125rem solid #222;
    padding: 0.625rem;
    font-size: 1rem;
    margin: 0 auto;
    cursor: pointer;
    transition: 0.5s;
  }

  .submit:hover {
    background-color: transparent;
    color: #222;
  }
</style>