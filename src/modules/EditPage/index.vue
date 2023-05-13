<script>
import Button from '../../components/Button';

export default {
  name: 'EditPage',
  props: {
    selectedCar: { type: Object, required: true }
  },
  components: { Button },
  data() {
    return {
      car: null,
      colors: ['red', 'blue', 'green', 'black', 'orange', 'purple', 'brown'],
    };
  },
  created() {
    this.car = Object.assign({}, this.selectedCar);
  },
  methods: {
    cancel() {
      this.$emit('cancel');
    },
    save() {
      this.$emit('updateCar', this.car);
    },
  },
  computed: {
    hpRangeErrorVisible() {
      return this.car.hp < 100 || this.car.hp > 550;
    },
    saveButtonDisable() {
      return this.hpRangeErrorVisible || this.car === this.selectedCar;
    },
  },
}
</script>

<template>
  <div class="edit-page">
    <div class="edit-page__form">
      <p><b>ID:</b> {{ car.id }}</p>
      <p><b>CAR:</b> {{ car.carId }}</p>
      <p>
        <b>INSTOCK:</b>
        <input type="checkbox" id="checkbox" v-model="car.inStock" />
      </p>
      <p>
        <b>HORSE POWER:</b>
        <input v-model.number="car.hp" class="text-input" />
        <span v-show="hpRangeErrorVisible" class="error-text">
          * Please write value between 100 - 550
        </span>
      </p>
      <p>
        <b>PRICE:</b>
        <input v-model.number="car.price" class="text-input" />
      </p>
      <p><br><b>COLOR:</b></p>
      <div v-for="(color, index) in colors" :key="index">
        <input type="radio" :id="color" :value="color" v-model="car.color" />
        <label :for="color" :style="{ color: color }">
          <b>{{ color }}</b>
        </label>
      </div>
    </div>

    <div class="edit-page__actions">
      <Button text="Cancel" @click="cancel" cancel />
      <Button text="Save" @click="save" :disabled="saveButtonDisable" />
    </div>
  </div>
</template>

<style lang="scss">
.edit-page {
  text-align: start;

  input {
    margin-left: 0.5rem;
    min-width: 1rem;
    margin-top: 0.5rem;
  }
  
  .error-text {
    color: #e00000
  }
  
  .text-input {
    display: flex;
    font-size: 1.2rem;
    margin: 0.5rem 0;
    border-radius: 0.5rem;
    color: #444;
    padding: 0.5rem;
    border: 1px solid #444;
  }

  &__actions {
    gap: 1rem;
    display: flex;
    margin-top: 2rem;
  }
}
</style>
