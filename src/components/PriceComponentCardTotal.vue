<template>
  <div>total : {{ total }}</div>
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
      return this.items
        .reduce((acc, curr) => Number(acc) + Number(curr.value), this.basePrice)
        .toFixed(2)
    },
  },
}
</script>

<style></style>
