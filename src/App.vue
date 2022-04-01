<template>
  <nav class="navbar navbar-light bg-light">
    <div class="container-fluid ">
      <button type="button" class="btn btn-primary" aria-label="Close" @click="navigateBack">Back</button>
    </div>
  </nav>
  <router-view/>
</template>

<script>

export default {
  name: 'App',
  methods: {
    navigateBack() {
      window.history.go(-1)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
