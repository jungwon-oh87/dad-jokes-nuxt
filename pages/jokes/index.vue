<template>
  <div>
    <Joke v-for="joke in jokes" :key="joke.id" :joke="joke.joke" />
  </div>
</template>

<script>
import axios from "axios";
import Joke from "../../components/Joke";

export default {
  data() {
    return {
      jokes: []
    };
  },
  async created() {
    try {
      const res = await axios.get("https://icanhazdadjoke.com/search", {
        headers: {
          Accept: "application/json"
        }
      });
      this.jokes = res.data.results;
      console.log(this.jokes);
    } catch (err) {
      console.log(err);
    }
  }
};
</script>

<style></style>
