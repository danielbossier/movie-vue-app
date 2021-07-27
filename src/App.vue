<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      |
      <router-link to="/signup">Signup</router-link>
      |
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/logout">Logout</router-link>
      |
      <router-link to="/movies">Movies</router-link>
      |
      <router-link to="/movies/new">Create</router-link>
    </div>
    <router-view />
  </div>
</template>

<style>
body {
  background-image: url("./assets/cloudy-day.png");
  color: rgb(36, 117, 203) !important;
  font-family: Garamond, Baskerville, Baskerville Old Face, Hoefler Text, Times New Roman, serif !important;
  text-align: center;
}
</style>
