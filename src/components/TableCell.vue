<template>
  <div class="tableCell">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "TableCell",
};
</script>

<style scoped>
.tableCell {
  width: calc(100vw / 7);
  border: 1px solid black;
  display: flex;
  align-items: center;
  justify-content: center;
}

.tableCell:first-child {
  font-weight: bold;
}
</style>
