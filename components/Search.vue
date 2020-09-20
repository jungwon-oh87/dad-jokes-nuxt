<template>
  <form @submit="search">
    <label>Search Jokes</label>
    <input type="text" v-model="searchInput" />
    <input type="submit" value="Submit" />
  </form>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      searchInput: "",
    };
  },
  methods: {
    search: function (e) {
      e.preventDefault();
      this.$emit("search-text", this.searchInput);
      this.searchInput = "";
      //   console.log("search called, ", this.searchInput);
    },
  },
};
</script>

<style>
</style>