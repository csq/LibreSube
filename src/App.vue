<template>
  <nav class="navbar" style="background-color: #0e8ccc;">
    <div class="container-fluid mx-sm-1 mx-md-3 mx-lg-5">
      <router-link style="text-decoration: none;" to="/">Inicio</router-link> |
      <router-link style="text-decoration: none;" to="/charge-points">Puntos de carga</router-link> |
      <router-link style="text-decoration: none;" to="/tas">Terminales TAS</router-link> |
      <router-link style="text-decoration: none;" to="/data">Info</router-link>
    </div>
  </nav>
  <div class="container pt-1 pb-5">
    <router-view/>
  </div>
  <Footer></Footer>
</template>

<script>
import Footer from './components/FooterSegment'

export default {
  components: {
      Footer
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
  color: #ffffff;
}

nav a.router-link-exact-active {
  color: #292b23;
}
</style>
