<template>
  <div class="price-component-card">
    <PriceComponentCardTotal :items="items" />
    <PriceComponentCardEntries
      :itemBeingEditedId="itemBeingEditedId"
      :items="items"
      @row-to-remove="removeRow"
      @row-to-edit="editRow"
    />
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
      itemBeingEditedId: undefined,
    }
  },
  methods: {
    updateItems(payload) {
      this.items.push(payload)
    },
    removeRow(id) {
      this.items = this.items.filter((item) => item.id !== id)
    },
    editRow(id) {
      this.items.forEach((item) => {
        if (item.id === id) {
          item.isEdit = !item.isEdit
          this.itemBeingEditedId = item.id
        }
      })
    },
  },
}
</script>

<style scoped>
.price-component-card {
  padding: 40px 60px;
  background-color: papayawhip;
  height: 80vh;
  min-width: 500px;
  width: 60vw;
  display: flex;
  flex-direction: column;
}
</style>
