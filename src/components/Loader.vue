<script>
export default {
  name: 'Loader',
}
</script>

<template>
  <div class="app-loader" />
</template>

<style lang="scss">
.app-loader {
  border: 5px solid #f3f3f3;
  border-top: 5px solid #3498db;
  border-radius: 50%;
  width: 32px;
  height: 32px;
  animation: spin 1.2s linear infinite;

  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
}
</style>
