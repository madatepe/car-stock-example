<script>
import EntryPage from '../modules/EntryPage'
import EditPage from '../modules/EditPage'

export default {
  name: 'Container',
  components: { EntryPage, EditPage },
  data() {
    return {
      editMode: false,
      selectedCar: null,
    };
  },
  methods: {
    editCar(car) {
      this.selectedCar = car;
      this.editMode = true;
    },
  },
}
</script>

<template>
  <div class="app-container">
    <EditPage v-if="editMode" :selected-car="selectedCar" />
    <EntryPage v-else @editCar="editCar" />
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
