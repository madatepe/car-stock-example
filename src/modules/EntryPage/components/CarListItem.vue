<script>
import Button from '../../../components/Button';

export default {
  name: 'CarListItem',
  props: {
    car: { type: Object, required: true },
  },
  components: {
    Button,
  },
  computed: {
    inStockSvgUrl() {
      return this.car.inStock ? '/svg/check.svg' : '/svg/cancel.svg';
    },
  },
  methods: {
    editItem() {
      this.$emit("editItem", this.car);
    },
  },
}
</script>

<template>
  <tr class="car-list-item">
    <td class="car-id"><b>{{ car.id }}</b></td>
    <td>{{ car.carId }}</td>
    <td class="in-stock">
      <img class="in-stock__svg" :src="inStockSvgUrl">
    </td>
    <td>{{ car.hp }}</td>
    <td>{{ car.price }}$</td>
    <td class="color" :style="{ color: car.color }">
      &bull;
    </td>
    <td class="edit">
      <Button text="Edit" @click="editItem" />
    </td>
  </tr>
</template>

<style lang="scss">
.car-list-item {
  border-bottom: 1px solid #F1F1F1;
  color: #1c1c1c;
  
  td {
    border-radius: 0.5rem;
    padding: 0.5rem;
    border: 1px solid #F1F1F1;
  }

  .car-id {
    width: 5%;
  }

  .in-stock {
    width: 5%;

    &__svg {
      width: 1.5rem;
      height: 1.5rem;
    }
  }

  .color {
    width: 5%;
    font-size: 2.3rem;
    padding: 0;
    margin: 0;
  }
  
  .edit {
    width: 10%;
  }
}
</style>
