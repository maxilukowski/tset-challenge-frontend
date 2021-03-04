<template>
  <form class="ghost-fields-row" @submit.prevent="submit">
    <div>
      <input
        type="text"
        placeholder="label"
        v-model="ghostField.label"
        required
      />
      <input
        type="number"
        placeholder="0"
        v-model.number="ghostField.value"
        step="any"
        min="0"
        required
      />
    </div>
    <button>submit</button>
  </form>
</template>

<script>
import { uuid } from 'vue-uuid'
export default {
  data() {
    return {
      ghostField: {
        label: undefined,
        value: undefined,
        isHover: false,
        formattedValue: undefined,
      },
    }
  },
  methods: {
    submit() {
      this.ghostField.formattedValue = this.formatValue
      this.$emit('ghost-field-values', {
        ...this.ghostField,
        id: uuid.v4(),
      })
      this.ghostField.label = ''
      this.ghostField.value = ''
    },
  },
  computed: {
    formatValue() {
      const hasDecimal = this.ghostField.value.toString().includes('.')
      if (hasDecimal) {
        const hasMultipleDecimals =
          this.ghostField.value.toString().split('.')[1].length > 1
        if (hasMultipleDecimals) return this.ghostField.value.toFixed(2)
        else return this.ghostField.value.toFixed(1)
      }
      return this.ghostField.value.toFixed(1)
    },
  },
}
</script>

<style scoped>
.ghost-fields-row {
  display: flex;
  justify-content: space-between;
}
</style>
