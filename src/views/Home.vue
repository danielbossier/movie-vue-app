<template>
  <div class="home">
    <h2>Add a flick!</h2>
    <button v-on:click="createMovie()">Add that Movie</button>
    <h1>{{ message }}</h1>
    <div v-for="movie in movies" :key="movie.id">
      <h2>Title: {{ movie.title }}</h2>
      <h3>Plot: {{ movie.plot }}</h3>
      <br />
    </div>
  </div>
</template>
<style></style>
<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Watch these movies, sucka!",
      movies: [],
    };
  },
  created: function () {
    this.indexMovies();
  },
  methods: {
    indexMovies: function () {
      axios.get("http://localhost:3000/movies").then((response) => {
        this.movies = response.data;
        console.log("All Movies:", this.movies);
      });
    },
    createMovie: function () {
      console.log("added that movie, baybay!");

      var params = {
        title: "A Clockwork Orange",
        year: 1971,
        plot: "Alex DeLarge has a thirst for milk and a bit of old ultra-violence.",
        director: "Stanley Kubrick",
      };
      axios
        .post("http://localhost:3000/movies", params)
        .then((response) => {
          console.log("Success!", response.data);
          this.movies.push(response.data);
        })
        .catch((error) => console.log(error.response));
    },
  },
};
</script>
