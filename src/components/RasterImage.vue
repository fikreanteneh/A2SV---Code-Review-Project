<template>
  <h1>{{ stepsTaken }}</h1>
  <h1>{{ xIncrement }}</h1>
  <h1>{{ yIncrement }}</h1>
</template>
<script>
export default {
  props: ["stepsTaken", "xIncrement", "yIncrement"],
};
</script>
<style></style>
