<template>
  <div>total : {{ formatTotal }}</div>
</template>

<script>
export default {
  props: {
    items: Array,
  },
  data() {
    return {
      basePrice: 1,
    }
  },
  computed: {
    total() {
      return this.items.reduce(
        (acc, curr) => Number(acc) + Number(curr.formattedValue),
        this.basePrice
      )
    },
    formatTotal() {
      const hasDecimal = this.total.toString().includes('.')
      if (hasDecimal) {
        const hasMultipleDecimals =
          this.total.toString().split('.')[1].length > 1
        if (hasMultipleDecimals) return this.total.toFixed(2)
        else return this.total
      }
      return this.total.toFixed(1)
    },
  },
}
</script>

<style></style>
