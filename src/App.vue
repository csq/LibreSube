<template>
  <Navbar></Navbar>
  <div class="container pt-1 pb-5">
    <router-view/>
  </div>
  <Footer></Footer>
</template>

<script>
import Navbar from './components/NavBarSegment'
import Footer from './components/FooterSegment'

export default {
  components: {
    Navbar,
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
</style>
