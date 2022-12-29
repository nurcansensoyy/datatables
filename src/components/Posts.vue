<template></template>

<script>
import axios from "axios";

export default {
  name: "app",
  data() {
    return {
      url: "http://www.omdbapi.com/?apikey=c5b429de&type=movie&s=comedy",
      movies: [],
    };
  },
  created() {
    axios.post(this.url).then((response) => (this.movies = response.data));
  },
};
</script>

<style></style>
