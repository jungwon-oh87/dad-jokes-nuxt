<template>
  <div>{{ this.singleJoke }}</div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      singleJoke: "",
    };
  },
  async create() {
    const res = await axios.get(
      `https://icanhazdadjoke.com/j/${$route.params.id}`,
      {
        headers: {
          Accept: "application/json",
        },
      }
    );
    console.log("res: ", res);
    singleJoke = res.data;
    console.log("singleJoke: ", singleJoke);
  },
};
</script>

<style></style>
