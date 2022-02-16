<script>
import axios from "axios";
export default {
  data: function () {
    return {
      movie: {}
    };
  },
  created: function () {
    axios.get(`/movies/${this.$route.params.id}`).then((response) => {
      console.log("Movies Show:", response.data);
      this.movie = response.data;
    });
  },
  methods: {
    destroyMovie: function () {
      if (confirm("Are you sure you to delete this?")) {
        axios.delete(`/movies/${this.movie.id}`).then((response) => {
          console.log("Success", response.data);
          this.$router.push("/movies");
        });
      }
    },
  },
};
</script>

<template>
  <div class="movies-show">
    <h2>{{ movie.title }}</h2>
    <img v-bind:src="movie.image_url" alt="" />
    <p>Ingredients: {{ movie.ingredients }}</p>
    <p>Directions: {{ movie.directions }}</p>
    <p>Prep time: {{ movie.friendly_prep_time }}</p>
    <div v-if="movie.owner">
      <button>
        <router-link v-bind:to="`/movies/${movie.id}/edit`">Edit</router-link>
      </button>
      |
      <button v-on:click="destroyMovie()">Delete</button>
    </div>
  </div>
</template>