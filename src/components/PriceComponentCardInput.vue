<template>
  <form class="ghost-fields-row" @submit.prevent="submit">
    <div class="ghost-fields">
      <input type="text" placeholder="label" v-model="ghostField.label" />
      <input type="number" placeholder="value" v-model="ghostField.value" />
    </div>
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
        isHover: false,
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
.ghost-fields-row {
  display: flex;
  justify-content: space-between;
}
.ghost-fields {
  display: flex;
  justify-content: space-between;
}
</style>
