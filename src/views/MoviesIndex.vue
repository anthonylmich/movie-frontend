<script>
import axios from "axios";
export default {
  data: function () {
    return {
      movies: [],
    };
  },
  created: function () {
    axios.get("/movies").then((response) => {
      console.log("Movies Index:", response.data);
      this.movies = response.data;
    });
  },
};
</script>

<template>
  <div class="movies-index">
    <div v-for="movie in movies" v-bind:key="movie.id">
      <h2>{{ movie.title }}</h2>
      <router-link v-bind:to="`/movies/${movie.id}`"></router-link>
      <p>Year: {{ movie.year }}</p>
      <p>Plot: {{ movie.plot }}</p>
      <p>Director: {{ movie.director }}</p>
    </div>
  </div>
</template>
