<script>
import axios from "axios";

export default {
  data: function () {
    return {
      movie: {},
    };
  },
  created: function () {
    axios.get(`/movies/${this.$route.params.id}`).then((response) => {
      console.log("Movies Show:", response.data);
      this.movie = response.data;
    });
  },
  methods: {},
};
</script>

<template>
  <div class="movies-index">
    <h2>{{ movie.title }}</h2>
    <img v-bind:src="movie.image_url" alt="" />
    <p>Plot: {{ movie.plot }}</p>
    <p>Year: {{ movie.year }}</p>
    <p>Director: {{ movie.director }}</p>
    <div v-if="movie.owner">
      <button>
        <router-link v-bind:to="`/movies/${movie.id}/edit`">Edit</router-link>
      </button>
    </div>
  </div>
</template>
