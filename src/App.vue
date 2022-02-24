<script>
export default {
  data: function () {
    return {
      isLoggedIn: !!localStorage.jwt,
    };
  },
  watch: {
    $route: function () {
      this.isLoggedIn = !!localStorage.jwt;
    },
  },
};
</script>
<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">Home</router-link>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <div class="navbar-nav">
          <router-link class="nav-link" to="/movies">Movies</router-link>
          <router-link v-if="!isLoggedIn" class="nav-link" to="/signup"
            >Signup</router-link
          >
          <router-link v-if="!isLoggedIn" class="nav-link" to="/login"
            >Login</router-link
          >
          <router-link v-if="isLoggedIn" class="nav-link" to="/movies/new"
            >New Movie</router-link
          >
          <router-link v-if="isLoggedIn" class="nav-link" to="/logout"
            >Logout</router-link
          >
        </div>
      </div>
    </div>
  </nav>
  <router-view />
</template>

<!-- <style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style> -->
