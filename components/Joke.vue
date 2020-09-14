<template>
  <div class="container">{{ joke }}</div>
</template>

<script>
export default {
  name: "Joke",
  props: ["id", "joke"]
};
</script>

<style scoped>
.container {
  padding: 1rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>
