<script>
import Loader from '../../components/Loader';
import CarList from './components/CarList';

export default {
  name: 'EntryPage',
  components: {
    Loader,
    CarList,
  },
  data() {
    return {
      cars: [],
      isLoading: true,
    };
  },
  methods: {
    fetchData() {
      this.cars = [
        {
          id: 1,
          carId: 'AAA0',
          inStock: true,
          hp: 250,
          price: 50000,
          color: 'red',
        },
        {
          id: 2,
          carId: 'AAA1',
          inStock: false,
          hp: 140,
          price: 30000,
          color: 'blue',
        },
      ];

      setTimeout(() => {
        this.isLoading = false;
      }, 2200)
    },
  },
  mounted() {
    this.fetchData();
  },
}
</script>

<template>
  <div class="entry-page">
    <Loader v-if="isLoading" />
    <CarList v-else :cars="cars" />
  </div>
</template>

<style lang="scss">
.entry-page {
  display: flex;
  justify-content: center;
}
</style>
