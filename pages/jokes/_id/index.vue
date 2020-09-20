<template>
  <div>
    <nuxt-link to="/jokes">Back to Jokes List</nuxt-link>
    <br />
    <br />
    <p>{{this.singleJoke}}</p>
    <br />
    <hr />
    <small>joke id: {{$route.params.id}}</small>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      singleJoke: {},
    };
  },
  async created() {
    console.log("created called");
    try {
      const res = await axios.get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        {
          headers: {
            Accept: "application/json",
          },
        }
      );
      console.log("res: ", res);
      this.singleJoke = res.data.joke;
    } catch (error) {
      console.log(error);
    }
    console.log("singleJoke: ", this.singleJoke);
  },
};
</script>

<style></style>
