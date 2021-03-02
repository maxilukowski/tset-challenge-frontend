<template>
  <div id="app">
    <PriceComponentCard />
  </div>
</template>

<script>
import PriceComponentCard from './components/PriceComponentCard.vue'
export default {
  name: 'App',
  components: { PriceComponentCard },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
}
</style>
