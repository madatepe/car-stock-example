<script>
export default {
  name: 'Button',
  props: {
    text: { type: String, required: false, default: 'Action!' },
    color: { type: String, required: false, default: '#3498db' },
  },
}
</script>

<template>
  <button
    class="app-button"
    :style="{ backgroundColor: color }"
    v-on="$listeners"
  >
    {{ text }}
  </button>
</template>

<style lang="scss">
.app-button {
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
</style>
