<template>
  <div id="app">
    <InputFields :months="months" @monthInput="handleMonthChange" @personInput="handlePersonChange"/>
    <TableHeader :month="months[month]"></TableHeader>
    <TableRow
      v-for="day in daysInMonth"
      :key="day"
      :day="day"
      :year="year"
      :month="month"
      :dayPrefix="getDayPrefix(day)"
      :weekIdx="getWeekIdx(day)"
      :lateShiftIdx="lateShiftIdx"
    >
    </TableRow>
  </div>
</template>

<script>
import TableRow from "./components/TableRow.vue";
import TableHeader from "./components/TableHeader.vue";
import InputFields from "./components/InputFields.vue";

export default {
  name: "App",
  components: {
    TableRow,
    TableHeader,
    InputFields
  },
  data: () => ({
    month: 0,
    year: 2021,
    days: ["X", "Pn.", "Wt.", "Śr.", "Cz.", "Pt.", "X"],
    months: ['Styczeń', 'Luty', 'Marzec', 'Kwiecień', 'Maj', 'Czerwiec', 'Lipiec', 'Sierpień', 'Wrzesień', 'Październik', 'Listopad', 'Grudzień'],
    lateShiftIdx: 2,
    weekIdx: 0
  }),
  mounted() {
    console.log(new Date(this.year, this.month, 4));
    console.log(this.daysInMonth);
    console.log(new Date());

  },
  computed: {
    daysInMonth() {
      console.log('month: ', this.month, 'days ', new Date(this.year, this.month + 1, 0).getDate())
      return new Date(this.year, this.month + 1, 0).getDate();
    },
    // computedLateShiftIdx(day) {
    //
    // }
  },
  methods: {
    getDayPrefix(day) {
      return this.days[new Date(this.year, this.month, day).getDay()];
    },
    getWeekIdx(day) {
      let helpArr = []
      for(let i = 1; i <= day; i++) {
        helpArr.push(this.getDayPrefix(i))
      }
      return helpArr.filter(item => item === 'Pn.').length
    },
    handleMonthChange(value) {
      this.month = +value
    },
    handlePersonChange(value) {
      this.lateShiftIdx = +value
    }
  },
};
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: "Arial", sans-serif;
  width: 100vw;
}


</style>
