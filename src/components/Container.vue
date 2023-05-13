<script>
import EntryPage from '../modules/EntryPage'
import EditPage from '../modules/EditPage'

export default {
  name: 'Container',
  components: {
    EntryPage,
    EditPage,
  }
}
</script>

<template>
  <div class="app-container">
    <EntryPage />
    <EditPage />
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
