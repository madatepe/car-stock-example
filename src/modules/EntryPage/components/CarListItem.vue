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
  methods: {
    editItem() {
      this.$emit("editItem", this.car);
    },
  },
}
</script>

<template>
  <tr class="car-list-item">
    <td class="car-id">{{ car.carId }}</td>
    <td>{{ car.id }}</td>
    <td class="in-stock">{{ car.inStock }}</td>
    <td>{{ car.hp }}</td>
    <td>{{ car.price }}</td>
    <td>{{ car.color }}</td>
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
    padding: 10px;
    border: 1px solid #F1F1F1;
  }

  .car-id {
    width: 5%;
  }

  .in-stock {
    width: 5%;
  }
  
  .edit {
    width: 10%;

    &-button {
      
    }
  }
}
</style>
