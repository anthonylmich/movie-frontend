<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      movies: [],
    };
  },
  created: function () {
    this.indexMovies();
  },
  methods: {
    indexMovies: function () {
      console.log("hello");
      axios.get("https://localhost:3000/movies").then((response) => {
        console.log(response.data);
        this.movies = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
  </div>
  <div>
    <p>Sanity check</p>
  </div>
  <div v-for="movie in movies" v-bind:key="movie.id">
  <h2>Movie: {{ movie.title }}</h2>
  <p>Plot: {{ movie.plot }}</p>
  </div>
  <button v-on:click="indexMovies()">Index</button>
</template>

<style></style>
