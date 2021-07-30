<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="#">Movie-Bar</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNavDropdown"
        aria-controls="navbarNavDropdown"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <a class="nav-link" href="/movies">Movies</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/about">About</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/movies/new">Create</a>
          </li>
          <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle"
              href="#"
              id="navbarDropdownMenuLink"
              role="button"
              data-bs-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >
              Users!
            </a>
            <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <li v-if="!isLoggedIn()">
                <a class="dropdown-item" href="/signup">Signup</a>
              </li>
              <li v-if="!isLoggedIn()">
                <a class="dropdown-item" href="/login">Login</a>
              </li>
              <li v-if="isLoggedIn()">
                <a class="dropdown-item" href="/logout">Logout</a>
              </li>
            </div>
          </li>
        </ul>
      </div>
    </nav>

    <!-- <div id="nav">
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
    </div> -->
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

<script>
export default {
  methods: {
    isLoggedIn: function () {
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
    getUserId: function () {
      return localStorage.getItem("user_id");
    },
  },
};
</script>
