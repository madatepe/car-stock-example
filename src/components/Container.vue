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
        axios.get('https://run.mocky.io/v3/ae1904d5-ecf2-460e-be1b-860b9d9cd9b3')
          .then(({ data }) => {
            this.cars = data;
          })
          .catch(() => {})
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
