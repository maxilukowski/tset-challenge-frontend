<template
  ><div>
    <div v-for="(item, index) in items" :key="index" class="entry-row">
      <div>{{ item.label }}</div>
      <div>{{ item.value }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    items: Array,
  },
}
</script>

<style scoped>
.entry-row {
  display: flex;
  justify-content: space-between;
}
</style>
