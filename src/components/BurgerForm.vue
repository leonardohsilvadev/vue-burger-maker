<template>
  <div>
    <Message v-show="message" :message="message" />
    <form id="form" @submit="handleAddBurger">
       <div class="input-container">
         <label for="name">Name</label>
         <input type="text" name="name" v-model="name" placeholder="enter your name" />
       </div>

        <div class="input-container">
         <label for="bread">Choose the bread</label>
         <select name="bread" v-model="bread">
           <option :key="bread.id" v-for="bread in breads">{{ bread.type }}</option>
         </select>
       </div>

        <div class="input-container">
         <label for="meat">Choose the meat</label>
         <select name="meat" v-model="meat">
           <option :key="meat.id" v-for="meat in meats">{{ meat.type }}</option>
         </select>
       </div>

       <div id="optionals-container" class="input-container">
         <label id="optionals-title" for="optionals">Choose the optionals</label>
         <div :key="optional.id" v-for="(optional, index) in optionals" class="checkbox-container" @click="handleCheckOptional(index)">
           <input type="checkbox" :name="optional.type" :value="optional.type" :checked="optional.checked" />
           <span>{{ optional.type }}</span>
         </div>

         <div class="input-container">
           <input type="submit" class="submit" value="place order">
         </div>
       </div>
    </form>
  </div>
</template>

<script>
import Message from './Message.vue'
import { api } from '../utils/api'

export default {
  name: 'BurgerForm',
  components: {
    Message
  },
  data() {
    return {
      breads: [],
      meats: [],
      optionals: [],
      name: '',
      bread:'',
      meat: '',
      message: ''
    }
  },
    methods: {
    async getIngredients() {
      const url = 'ingredients'

      await api
        .get(url)
        .then(({ data: { meats, optionals, breads } }) => {
          this.breads = breads;
          this.meats = meats;
          this.optionals = optionals.map(o => ({ ...o, checked: false }))
          })
        .catch(err => console.log('err: ', err))
    },
    async handleAddBurger(e) {
      e.preventDefault();
      const url = 'burgers'
      const data = {
        name: this.name,
        meat: this.meat,
        bread: this.bread,
        optionals: this.optionals.filter(({ checked }) => checked).map(({ type }) => type),
        status: 'Requested'
      }

      await api
        .post(url, data)
        .then(() => {
          this.name = ''
          this.bread = ''
          this.meat = ''
          this.optionals = this.optionals.map(o => ({ ...o, checked: false }))
          this.handleSuccessMessage()
        })
        .catch(err => console.log('err: ', err))
    },
    handleCheckOptional(index) {
      this.optionals[index].checked = !this.optionals[index].checked
    },
    handleSuccessMessage() {
      this.message = 'Order successfully placed'
      setTimeout(() => {
        this.message = ''
      }, 3000)
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