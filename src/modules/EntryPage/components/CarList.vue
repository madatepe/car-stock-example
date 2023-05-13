<script>
import CarListHeader from './CarListHeader';

export default {
  name: 'CarList',
  components: {
    CarListHeader,
  },
  props: {
    cars: { type: Array, required: false, default: () => [] }
  },
}
</script>

<template>
  <div class="car-list">
    <table class="car-list__table">
      <caption class="car-list__caption">Car list</caption>
      <CarListHeader />
      <tbody>
        <tr>
          <th>0</th>
          <th>AAA0</th>
          <td>true</td>
          <td>250</td>
          <td>250</td>
          <td>red</td>
          <td>edit</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style lang="scss">
.car-list {
  width: 100%;
  
  &__table {
    width: inherit; 
  }

  &__caption {
    text-transform: uppercase;
    font-weight: bold;
    font-size: 1.5rem;
    color: #3498db;
  }
}
</style>
