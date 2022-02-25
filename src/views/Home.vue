<!-- <script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      movies: [],
      params: {},
      currentMovie: {},
      params2: {},
    };
  },
  created: function () {
    this.indexMovie();
  },
  // methods: {
  //   indexMovie: function () {
  //     console.log("sanity ..");
  //     axios.get("http://localhost:3000/movies").then((response) => {
  //       console.log(response.data);
  //       this.movies = response.data;
  //     });
  //   },
  //   createMovie: function () {
  //     axios
  //       .post("http://localhost:3000/movies", this.params)
  //       .then((response) => {
  //         console.log(response.data);
  //         this.movies.push(response.data);
  //       })
  //       .catch((error) => {
  //         console.log(error.response.data.errors);
  //       });
  //     this.indexMovie();
  //   },
  //   showMovie: function (movie) {
  //     console.log(movie);
  //     this.currentMovie = movie;
  //     this.params2 = movie;
  //     document.querySelector("#movie-details").showModal();
  //   },
  //   updateMovie: function (movie) {
  //     axios
  //       .patch(`http://localhost:3000/movies/${movie.id}`, movie)
  //       .then((response) => {
  //         console.log(response.data);
  //       });
  //   },
  //   destroyMovie: function (movie) {
  //     if (confirm("Are you sure you want to delete this?")) {
  //       axios
  //         .delete(`http://localhost:3000/movies/${movie.id}`)
  //         .then((response) => {
  //           console.log(response.date);
  //           var index = this.movies.indexOf(movie);
  //           this.movies.splice(index, 1);
  //         });
  //     }
  //   },
  // },
};
//
</script>

//
<template>
  //
  <div class="home">
    //
    <h1>{{ message }}</h1>
    //
  </div>
  //
  <div>Title: <input type="text" v-model="params.title" /></div>
  //
  <div>Director: <input type="text" v-model="params.director" /></div>
  //
  <div>Year: <input type="text" v-model="params.year" /></div>
  //
  <div>Plot: <input type="text" v-model="params.plot" /></div>
  // <button v-on:click="createMovie()">Create</button> //
  <div v-for="movie in movies" v-bind:key="movie.id">
    //
    <h2>Movie: {{ movie.title }}</h2>
    //
    <p>Director: {{ movie.director }}</p>
    // <button v-on:click="showMovie(movie)">More Info</button> //
    <div>
      //
      <dialog id="movie-details">
        //
        <form method="dialog">
          //
          <h2>Movie Info</h2>
          //
          <p>Title: <input type="text" v-model="params2.title" /></p>
          //
          <p>Director: <input type="text" v-model="params2.director" /></p>
          //
          <p>Year: <input type="text" v-model="params2.year" /></p>
          //
          <p>Plot: <input type="text" v-model="params2.plot" /></p>
          // <button v-on:click="updateMovie(currentMovie)">Update</button> //
          <button v-on:click="destroyMovie(currentMovie)">Delete</button> //
          <button>Close</button> //
        </form>
        //
      </dialog>
      //
    </div>
    //
  </div>
  //
</template>

//
<style></style> -->
