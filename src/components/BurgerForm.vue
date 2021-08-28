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
           <option :key="bread.id" v-for="bread in breads">{{ bread.tipo }}</option>
         </select>
       </div>

        <div class="input-container">
         <label for="meat">Choose the meat</label>
         <select name="meat" v-model="meat">
           <option :key="meat.id" v-for="meat in meats">{{ meat.tipo }}</option>
         </select>
       </div>

       <div id="optionals-container" class="input-container">
         <label id="optionals-title" for="optionals">Choose the optionals</label>
         <div :key="optional.id" v-for="optional in optionals" class="checkbox-container">
           <input type="checkbox" :name="optional.tipo" v-model="selectedOptionals" :value="optional.tipo" />
           <span>{{ optional.tipo }}</span>
         </div>

         <div class="input-container">
           <input type="submit" class="submit" value="place order">
         </div>
       </div>
    </form>
  </div>
</template>

<script>
import { api } from '../utils/api'

export default {
  name: 'BurgerForm',
  data() {
    return {
      breads: [],
      meats: [],
      optionals: [],
      name: '',
      bread:'',
      meat: '',
      selectedOptionals: []
    }
  },
    methods: {
    async getIngredients() {
      await api
        .get('ingredientes')
        .then(({ data: { carnes, opcionais, paes } }) => {
          console.log('carnes: ', carnes);
          console.log('opcionais: ', opcionais);
          console.log('paes: ', paes);
          this.breads = paes;
          this.meats = carnes;
          this.optionals = opcionais;
          })
        .catch(err => console.log('err: ', err))
    }
  },
  mounted() {
    this.getIngredients()
  }
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