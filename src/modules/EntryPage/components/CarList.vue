<script>
import CarListHeader from './CarListHeader';
import CarListItem from './CarListItem';

export default {
  name: 'CarList',
  components: {
    CarListHeader,
    CarListItem,
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
        <CarListItem
          v-for="car in cars"
          :key="car.id"
          :car="car"
          @editItem="$emit('editCar', $event)"
        />
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
    border-bottom: 2px solid #fab700;
    padding-bottom: 1rem;
  }
}
</style>
