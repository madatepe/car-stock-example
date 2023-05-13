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
      hpRangeErrorVisible: false,
      colors: [
        'red',
        'blue',
        'green',
        'black',
        'orange',
        'purple',
        'brown',
      ],
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
  watch: {
    'car.hp'(newVal) {
      if (newVal < 100 || newVal > 550) {
        this.hpRangeErrorVisible = true;
      }
    }
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
        <input v-model.number="car.hp" />
        <span v-show="hpRangeErrorVisible" class="error-text">
          * Please write value between 100 - 550
        </span>
      </p>
      <p>
        <b>PRICE:</b>
        <input v-model.number="car.price" />
      </p>
      <p><b>COLOR:</b></p>
      <div v-for="(color, index) in colors" :key="index">
        <input type="radio" :id="color" :value="color" v-model="car.color" />
        <label :for="color" :style="{ color: color }">
          <b>{{ color }}</b>
        </label>
      </div>
    </div>

    <div class="edit-page__actions">
      <Button color="#cf3131" text="Cancel" @click="cancel" />
      <Button text="Save" @click="save" />
    </div>
  </div>
</template>

<style lang="scss">
.edit-page {
  text-align: start;

  .error-text {
    color: #e00000
  }

  &__actions {
    gap: 1rem;
    display: flex;
    margin-top: 2rem;
  }
}
</style>
