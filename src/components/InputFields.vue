<template>
  <div class="wrapper">
    <select @input="$emit('monthInput', $event.target.value)">
      <option v-for="(month, idx) in months" :value="idx" :key="month">{{ month }}</option>
    </select>
    <select @input="$emit('personInput', $event.target.value)">
      <option value="1">Małgosia S.</option>
      <option value="2">Kamila</option>
      <option value="3">Krysia</option>
      <option value="4">Jola</option>
      <option value="0">Magda</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "InputFields",
  props: ['months'],
  emits: ['monthInput']
}
</script>

<style scoped>
  .wrapper {
    margin: 15px;
    display: flex;
    align-items: center;
    justify-content: space-around;
  }

  @media print {
    .wrapper {
      display: none;
    }
  }
</style>