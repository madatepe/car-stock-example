<script>
export default {
  name: 'CarListHeader',
}
</script>

<template>
  <thead class="car-list-header">
    <th>Id</th>
    <th>CarId</th>
    <th>In Stock</th>
    <th>Hp</th>
    <th>Price</th>
    <th>Color</th>
    <th>Edit</th>
  </thead>
</template>

<style lang="scss">
.car-list-header {
  text-transform: uppercase;

  th {
    text-transform: uppercase;
    text-align: center;
    padding: 0.5rem;
    color: #2779b0;
    border-bottom: 2px solid #fab700;
  }
}
</style>
