<template>
  <div class="tableRow">
    <TableCell>
      {{ fullDay }}
    </TableCell>
    <TableCell>
      {{ dayPrefix === 'X' ? 'X' : '6.30 - 14.30' }}
    </TableCell>
    <TableCell v-for="(value, idx) in orderedShifts" :key="value + idx">
      {{ dayPrefix === 'X' ? 'X' : value }}
    </TableCell>
  </div>
</template>

<script>
import TableCell from './TableCell';

export default {
  components: {
    TableCell,
  },
  props: ['day', 'dayPrefix', 'lateShiftIdx', 'weekIdx', 'year', 'month'],
  data: () => ({
    shifts: [
      '9.30 - 17.30 | O P',
      '7 - 15 | R O',
      '8 - 16 | O P',
      '7.30 - 15.30 | P',
      '7.30 - 15.30 | R',
    ],
  }),
  mounted() {
    this.getDay();
  },
  computed: {
    fullDay() {
      if (this.dayPrefix === 'X') return this.dayPrefix;
      return `${this.dayPrefix} ${this.day}`;
    },
    orderedShifts() {
      return this.moveDayForward(
        this.lateShiftIdx + this.getDay() + (this.weekIdx - 1),
      );
    },
  },
  methods: {
    moveDayForward(n) {
      let helperArr = [...this.shifts];
      for (let i = 0; i < n; i++) {
        helperArr.unshift(helperArr.splice(helperArr.length - 1, 1)[0]);
      }
      return helperArr;
    },
    getDay() {
      return new Date(this.year, this.month, this.day).getDay();
    },
  },
};
</script>

<style scoped>
.tableRow {
  height: calc(100vh / 32);
  width: 100%;
  /*background-color: lightgrey;*/
  display: flex;
}

.tableRow:nth-child(2n) {
  background-color: #eee;
}
</style>
