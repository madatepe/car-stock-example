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
  border-top: 2px solid #fab700;
  border-bottom: 2px solid #fab700;
  text-transform: uppercase;

  th {
    text-transform: uppercase;
    text-align: center;
    padding: 10px;
    color: #226896;
    border: 1px solid #F1F1F1;
  }
}
</style>
