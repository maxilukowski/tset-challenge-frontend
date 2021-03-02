<template>
  <div class="price-component-card">
    <PriceComponentCardTotal />
    <PriceComponentCardEntries :items="items" class="entries" />
    <PriceComponentCardInput @ghost-field-values="updateItems" />
  </div>
</template>

<script>
import PriceComponentCardEntries from './PriceComponentCardEntries.vue'
import PriceComponentCardInput from './PriceComponentCardInput.vue'
import PriceComponentCardTotal from './PriceComponentCardTotal.vue'
export default {
  components: {
    PriceComponentCardInput,
    PriceComponentCardEntries,
    PriceComponentCardTotal,
  },
  data() {
    return {
      items: [],
    }
  },
  methods: {
    updateItems(payload) {
      this.items.push(payload)
    },
  },
}
</script>

<style scoped>
.price-component-card {
  padding: 40px 60px;
  background-color: papayawhip;
  height: 80vh;
  width: 60vw;
  display: flex;
  flex-direction: column;
}
.entries {
  flex: 1;
}
</style>
