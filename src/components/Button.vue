<script>
export default {
  name: 'Button',
  props: {
    text: { type: String, required: false, default: 'Action!' },
    cancel: { type: Boolean, required: false, default: false },
    disabled: { type: Boolean, required: false, default: false },
  },
}
</script>

<template>
  <button
    class="app-button"
    :disabled="disabled"
    :class="{
      'app-button__cancel': cancel,
      'app-button__disabled': disabled,
    }"
    v-on="$listeners"
  >
    {{ text }}
  </button>
</template>

<style lang="scss">
.app-button {
  background: #3498db;
  border: none;
  color: #fff;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  font-weight: bold;

  &:hover {
    background: #2779b0;
    cursor: pointer;
  }
  
  &__cancel {
    background: #cf3131 !important;

    &:hover {
      background: #9d2626 !important;
    }
  }

  &__disabled {
    background: #a8a8a8 !important;
    pointer-events: none;
  }
}
</style>
