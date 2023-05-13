<script>
import EntryPage from '../modules/EntryPage'
import EditPage from '../modules/EditPage'
import Loader from '../components/Loader';
import axios from "axios";

export default {
  name: 'Container',
  components: { EntryPage, EditPage, Loader },
  data() {
    return {
      cars: [],
      carsIsLoading: true,
      editMode: false,
      selectedCar: null,
    };
  },
  methods: {
    fetchData() {
      // This timeout is added here to indicate an async process
      setTimeout(() => {
        // Expected Data: {"data":[{"id":1,"carId":"A1A1A1A1A1A1","inStock":true,"hp":140,"price":"10000$","color":"red"},{"id":2,"carId":"A2A2A2A2A2A2","inStock":false,"hp":250,"price":"5000$","color":"orange"},{"id":3,"carId":"A3A3A3A3A3A3","inStock":false,"hp":165,"price":"2350$","color":"red"},{"id":4,"carId":"A4A4A4A4A4A4","inStock":true,"hp":220,"price":"2000$","color":"blue"},{"id":5,"carId":"A5A5A5A5A5A5","inStock":true,"hp":182,"price":"1200$","color":"red"},{"id":6,"carId":"A6A6A6A6A6A6","inStock":false,"hp":250,"price":"5000$","color":"brown"},{"id":7,"carId":"A7A7A7A7A7A7","inStock":true,"hp":200,"price":"21000$","color":"purple"}]}
        axios.get('https://run.mocky.io/v3/25ca1565-a7d6-4d36-8491-9355a64a9bb5')
          .then(({ data }) => {
            this.cars = data.data;
          })
          .catch((error) => {
            alert(error.message)
          })
          .finally(() => {
            this.carsIsLoading = false;
          });
      }, 500)
    },
    editCar(car) {
      this.selectedCar = car;
      this.editMode = true;
    },
    closeEditMode() {
      this.selectedCar = null;
      this.editMode = false;
    },
    updateCar(newCar) {
      const foundIndex = this.cars.findIndex((car) => { return car.id === newCar.id });
      this.cars[foundIndex] = newCar;
      this.closeEditMode();
    },
  },
  mounted() {
    this.fetchData();
  },
}
</script>

<template>
  <div class="app-container">
    <EditPage
      v-if="editMode"
      :selected-car="selectedCar"
      @cancel="closeEditMode"
      @updateCar="updateCar"
    />
    <Loader v-else-if="carsIsLoading" />
    <EntryPage v-else :cars="cars" @editCar="editCar" />
  </div>
</template>

<style lang="scss">
.app-container {
  border: 1px solid #d8d8d8;
  border-radius: 0.5rem;
  min-height: 45rem;
  padding: 1rem;
  text-align: center;
}
</style>
