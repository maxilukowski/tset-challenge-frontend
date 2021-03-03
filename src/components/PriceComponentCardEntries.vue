<template
  ><div class="entries">
    <div class="entry-row">
      <div class="row-values">
        <div class="entry-label">baseprice</div>
        <div class="entry-label">1</div>
      </div>
      <button v-show="isHover">trash</button>
    </div>
    <div v-for="(item, index) in items" :key="index" class="entry-row">
      <div
        class="row-values"
        @mouseenter="item.isHover = true"
        @mouseleave="item.isHover = false"
      >
        <div class="entry-label">{{ item.label }}</div>
        <div class="entry-label">{{ item.value }}</div>
        <button v-show="item.isHover" @click="deleteRow(item.id)">trash</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    items: Array,
  },
  data() {
    return {}
  },
  methods: {
    deleteRow(id) {
      this.items = this.items.filter((item) => item.id !== id)
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
