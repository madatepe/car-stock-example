<script>
import Container from './components/Container'

export default {
  name: 'App',
  components: {
    Container,
  }
}
</script>

<template>
  <div id="app">
    <Container />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 4rem 2rem;
}
</style>
