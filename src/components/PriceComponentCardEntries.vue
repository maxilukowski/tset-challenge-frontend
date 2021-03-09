<template
  ><div class="entries">
    <div class="entry-row">
      <div class="row-values">
        <div class="entry-label">baseprice</div>
        <div class="entry-label">1</div>
      </div>
    </div>
    <div
      v-for="item in items"
      :key="item.id"
      class="entry-row"
      @mouseenter="item.isHover = true"
      @mouseleave="item.isHover = false"
    >
      <div class="row-values">
        <input
          v-if="item.isEdit && itemBeingEditedId === item.id"
          type="text"
          v-model="item.label"
        />
        <div v-else class="entry-label">{{ item.label }}</div>
        <div class="entry-label">{{ item.formattedValue }}</div>
        <button v-show="item.isHover" @click="rowToRemove(item.id)">
          trash
        </button>
        <button v-show="item.isHover" @click="rowToEdit(item.id)">
          edit
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    items: Array,
    itemBeingEditedId: Boolean,
  },
  data() {
    return {}
  },
  methods: {
    rowToRemove(id) {
      this.$emit('row-to-remove', id)
    },
    rowToEdit(id) {
      this.$emit('row-to-edit', id)
    },
  },
}
</script>

<style scoped>
.entries {
  flex: 1;
}
.entry-row {
  display: flex;
  justify-content: space-between;
  margin: 10px 0;
}
.entry-label {
  flex: 0 0 150px;
}
.row-values {
  display: flex;
  justify-content: space-between;
}
</style>
/* this.items = this.items.filter((item) => item.id !== id) */
