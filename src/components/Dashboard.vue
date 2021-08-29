<template>
  <div :key="order.id" v-for="order in orders" id="burger-table">
    <div>
      <div id="burger-table-heading">
        <div class="order-id">#</div>
        <div>Client</div>
        <div>Bread</div>
        <div>Meat</div>
        <div>Optionals</div>
        <div>Actions</div>
      </div>
    </div>

    <div id="burger-table-rows">
      <div class="burger-table-row">
        <div class="order-number">{{ order.id }}</div>
        <div>{{ order.name }}</div>
        <div>{{ order.bread }}</div>
        <div>{{ order.meat }}</div>
        <div>
          <ul>
            <li :key="index" v-for="(optional, index) in order.optionals">{{ optional }}</li>
          </ul>
        </div>
        <div>
          <select
            name="status"
            class="status"
            @change="handleChangeOrderStatus(order.id, $event.target.value)"
          >
            <option
              :key="s.id"
              v-for="s in status"
              :value="s.type"
              :selected="getSelectedStatus(s.type, order.status)"
            >
              {{ s.type }}
            </option>
          </select>
          <button class="delete-btn" @click="handleDeleteOrder(order.id)">Cancel</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { api } from '../utils/api'

export default {
  name: 'Dashboard',
  data() {
    return {
      orders: [],
      status: []
    }
  },
  methods: {
    async getOrders() {
      const url = 'burgers'

      await api
        .get(url)
        .then(({ data }) => this.orders = data)
        .catch(err => console.log('err: ', err))
    },
    async getStatus() {
      const url = 'status'

      await api
        .get(url)
        .then(({ data }) => this.status = data)
        .catch(err => console.log('err: ', err))
    },
    async handleChangeOrderStatus(id, status) {
      const url = `burgers/${id}`
      const data = {
        status
      }

      await api
        .patch(url, data)
        .then(() => this.getOrders())
        .catch(err => console.log('err: ', err))
    },
    async handleDeleteOrder(id) {
      const url = `burgers/${id}`

      await api
        .delete(url)
        .then(() => this.getOrders())
        .catch(err => console.log('err: ', err))
    },
    getSelectedStatus(type, status) {
      return type === status
    }
  },
  mounted() {
    this.getOrders()
    this.getStatus()
  }
}
</script>

<style scoped>
  #burger-table {
    max-width: 75rem;
    margin: 0 auto;
  }

  #burger-table-heading,
  #burger-table-rows,
  .burger-table-row {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
  }

  #burger-table-heading {
    font-weight: bold;
    padding: 0.75rem;
    border-bottom: 0.188rem solid #333;
  }

  #burger-table-heading div,
  .burger-table-row div {
    width: 19%;
  }

  .burger-table-row {
    width: 100%;
    padding: 0.75rem;
    border-bottom: 0.063rem solid #CCC;
  }

  #burger-table-heading .order-id,
  .burger-table-row .order-number {
    width: 5%;
  }

  select {
    padding: 1rem 0.75rem;
    margin-right: 0.75rem;
  }

  .delete-btn {
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

  .delete-btn:hover {
    background-color: transparent;
    color: #222;
  }
</style>