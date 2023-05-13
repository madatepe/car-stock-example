<script>
export default {
  name: 'CarListItem',
  props: {
    car: { type: Object, required: true },
  },
  methods: {
    editItem() {
      this.emit("editItem", this.car);
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
      <button class="edit-button" @click="editItem">Edit</button>
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
      background-color: #3498db;
      border: none;
      color: #fff;
      padding: 0.5rem 1rem;
      border-radius: 0.5rem;
      font-weight: bold;
  
      &:hover {
        background: #2779b0;
        cursor: pointer;
      }
    }
  }
}
</style>
