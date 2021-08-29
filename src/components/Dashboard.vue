<template>
  <div id="burger-table">
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
        <div class="order-number">1</div>
        <div>Fabio</div>
        <div>Australiano</div>
        <div>Picanha</div>
        <div>
          <ul>
            <li>Cheddar</li>
            <li>Maionese</li>
          </ul>
        </div>
        <div>
          <select name="status" class="status">
          </select>
          <button class="delete-btn">Cancel</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Dashboard'
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
    padding: 1rem 3.25rem;
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