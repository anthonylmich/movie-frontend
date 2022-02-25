<script>
import axios from "axios";
export default {
  data: function () {
    return {
      newMovieParams: {},
      errors: [],
    };
  },
  methods: {
    createMovie: function () {
      axios
        .post("/movies", this.newMovieParams)
        .then((response) => {
          console.log("New Movie:", response.data);
          localStorage.setItem("flashMessage", "Movie successfully created!");
          this.$router.push("/movies");
        })
        .catch((error) => {
          this.errors = error.response.data;
        });
    },
  },
};
</script>

<template>
  <div class="container">
    <form v-on:submit.prevent="createMovie()">
      <h1>New Movie</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div class="mb-3">
        <label for="exampleInputTitle" class="form-label">Title</label>
        <input
          type="title"
          class="form-control"
          id="exampleInputTitle"
          aria-describedby="titleHelp"
          v-model="newMovieParams.title"
        />
        <div id="titleHelp" class="form-text">
          This is where you put the title of your Movie/post.
        </div>
      </div>
      <div class="mb-3">
        <label for="exampleInputPlot" class="form-label">Plot</label>
        <input
          type="plot"
          class="form-control"
          id="exampleInputPlot"
          aria-describedby="plotHelp"
          v-model="newMovieParams.plot"
        />
        <div id="plotHelp" class="form-text">
          This is where you put the plot of your Movie.
        </div>
      </div>
      <div class="mb-3">
        <label for="exampleInputDirector" class="form-label">Director</label>
        <input
          type="director"
          class="form-control"
          id="exampleInputDirector"
          aria-describedby="directorHelp"
          v-model="newMovieParams.director"
        />
        <div id="directorHelp" class="form-text">
          This is where you put the director of your Movie.
        </div>
      </div>
      <div class="mb-3">
        <label for="exampleInputYear" class="form-label">Year</label>
        <input
          type="year"
          class="form-control"
          id="exampleInputYear"
          aria-describedby="yearHelp"
          v-model="newMovieParams.year"
        />
        <div id="yearHelp" class="form-text">
          This is where you put the year of your Movie.
        </div>
      </div>

      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>

  <!-- <div class="movies-new">
    <form v-on:submit.prevent="createMovie()">
      <h1>New Movie</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div>
        <label>Title:</label>
        <input type="text" v-model="newMovieParams.title" />
      </div>
      <div>
        <label>Year:</label>
        <input type="text" v-model="newMovieParams.year" />
      </div>
      <div>
        <label>Plot:</label>
        <input type="text" v-model="newMovieParams.plot" />
      </div>
      <div>
        <label>Director:</label>
        <input type="text" v-model="newMovieParams.director" />
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div> -->
</template>
