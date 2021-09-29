<template>
  <div class="tableHeader">
    <TableCell>{{ month }}</TableCell>
    <TableCell v-for="name in headers" :key="name">
      {{ name }}
    </TableCell>
  </div>
</template>

<script>
import TableCell from "./TableCell";

export default {
  name: "TableHeader",
  props: ['month'],
  components: {
    TableCell,
  },
  data: () => ({
    headers: [
      "Małgosia C.",
      "Małgosia S.",
      "Kamila",
      "Krysia",
      "Jola",
      "Magda",
    ],
  }),
};
</script>

<style scoped>
.tableHeader {
  height: calc(100vh / 32);
  width: 100%;
  background-color: grey;
  font-weight: bold;

  display: flex;
}
</style>
