<template>
  <div>
    <Search v-on:search-text="searchApi" />
    <Joke v-for="joke in jokes" :key="joke.id" :joke="joke.joke" :id="joke.id" />
  </div>
</template>

<script>
import axios from "axios";
import Joke from "../../components/Joke";
import Search from "../../components/Search";
export default {
  data() {
    return {
      jokes: [],
    };
  },
  async created() {
    try {
      const res = await axios.get("https://icanhazdadjoke.com/search", {
        headers: {
          Accept: "application/json",
        },
      });
      this.jokes = res.data.results;
      // console.log(this.jokes);
    } catch (err) {
      console.log(err);
    }
  },
  methods: {
    async searchApi(searchInput) {
      console.log("searchInput: ", searchInput);
      try {
        const res = await axios.get(
          `https://icanhazdadjoke.com/search?term=${searchInput}`,
          {
            headers: {
              Accept: "application/json",
            },
          }
        );
        this.jokes = res.data.results;
        // console.log(this.jokes);
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style></style>
