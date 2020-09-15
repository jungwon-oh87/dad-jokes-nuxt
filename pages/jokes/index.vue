<template>
  <div>
    <h1>Jokes</h1>
    <Joke v-for="joke in jokes" :key="joke.id" :joke="joke.joke" />
  </div>
</template>

<script>
import axios from "axios";
import Joke from "../../components/Joke";

export default {
  components: {
    Joke
  },
  data() {
    return {
      jokes: []
    };
  },
  head() {
    return {
      title: "Dad Jokes",
      meta: [
        { charset: "utf-8" },
        { name: "viewport", content: "width=device-width, initial-scale=1" },
        {
          hid: "Daddy jokes collection",
          name: "description",
          content: "Daddy jokes collection"
        }
      ]
    };
  },
  methods: {
    async fetchApi() {
      try {
        const res = await axios.get("https://icanhazdadjoke.com/search", {
          headers: {
            Accept: "application/json"
          }
        });
        console.log("res.data: ", res.data);
        this.jokes = res.data.results;
        console.log("jokes data: ", this.jokes);
      } catch (err) {
        console.log(err);
      }
    }
  },
  created() {
    this.fetchApi();
  }
};
</script>

<style></style>
