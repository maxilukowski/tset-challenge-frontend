<template>
  <div class="ghost-fields">
    <input type="text" placeholder="label" v-model="ghostFields.label" />
    <input type="number" placeholder="value" v-model="ghostFields.value" />
  </div>
</template>

<script>
export default {
  props: {
    items: Array,
  },
  data() {
    return {
      ghostFields: {
        label: '',
        value: 0,
      },
    }
  },
}
</script>

<style scoped>
.ghost-fields {
  display: flex;
  justify-content: space-between;
}
</style>
