<template>
  <form class="ghost-fields" @submit.prevent="submit">
    <input type="text" placeholder="label" v-model="ghostField.label" />
    <input type="number" placeholder="value" v-model="ghostField.value" />
    <button>submit</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      ghostField: {
        label: '',
        value: 0,
      },
    }
  },
  methods: {
    submit() {
      this.$emit('ghost-field-values', { ...this.ghostField })
    },
  },
}
</script>

<style scoped>
.ghost-fields {
  display: flex;
  justify-content: space-between;
}
</style>
