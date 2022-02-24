<script>
import axios from "axios";
export default {
  data: function () {
    return {
      movies: [],
      search: "",
    };
  },
  created: function () {
    axios.get("/movies").then((response) => {
      console.log("Movies Index:", response.data);
      this.movies = response.data;
    });
  },
  methods: {
    filterMovies: function () {
      return this.movies.filter((movie) => {
        return movie.title.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
};
</script>

<template>
  <div class="container">
    <p>search: <input type="text" v-model="search" list="movieTitles" /></p>

    <datalist id="movieTitles">
      <option v-for="movie in movies" v-bind:key="movie.id">
        {{ movie.title }}
      </option>
    </datalist>
    <div v-for="movie in filterMovies()" v-bind:key="movie.id">
      <div class="col-sm-6">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">{{ movie.title }}</h5>
            <p class="card-text">
              {{ movie.plot }}
            </p>
            <a href="#" to="/movies/{{ movie.id }}" class="btn btn-primary"
              >View Movie</a
            >
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- <div class="movies-index">
    <h1>message</h1>
    <p>search: <input type="text" v-model="search" list="movieTitles" /></p>
    <datalist id="movieTitles">
      <option v-for="movie in movies" v-bind:key="movie.id">
        {{ movie.title }}
      </option>
    </datalist>
    <div v-for="movie in filterMovies()" v-bind:key="movie.id">
      <h2>{{ movie.title }}</h2>
      <button>
        <router-link v-bind:to="`/movies/${movie.id}`"></router-link>
      </button>
      <p>Year: {{ movie.year }}</p>
      <p>Plot: {{ movie.plot }}</p>
      <p>Director: {{ movie.director }}</p>
    </div>
  </div> -->
</template>
