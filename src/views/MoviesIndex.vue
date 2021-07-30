<template>
  <div class="movies-index">
    Search by title:
    <input v-model="titleFilter" />
    <div v-for="movie in filterBy(movies, titleFilter, 'title')" :key="movie.id">
      <router-link v-bind:to="`/movies/${movie.id}`">
        <h2>Title: {{ movie.title }}</h2>
        <p>Plot: {{ movie.plot }}</p>
      </router-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Vue2Filters from "vue2-filters";

export default {
  data: function () {
    return {
      titleFilter: "",
      movies: [],
    };
  },
  mixins: [Vue2Filters.mixin],
  created: function () {
    this.indexMovies();
  },
  methods: {
    indexMovies: function () {
      axios.get("http://localhost:3000/movies").then((response) => {
        this.movies = response.data;
        console.log("All movies:", this.movies);
      });
    },
  },
};
</script>
