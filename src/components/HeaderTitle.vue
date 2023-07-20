<template>
  <h1 class="text-center text-4xl text-orange-800 my-4">{{ title }}</h1>
</template>
<script>
export default {
  props: ["title"],
};
</script>
<style scoped>
h1 {
  font-family: "Bungee Inline", cursive;
}
</style>
