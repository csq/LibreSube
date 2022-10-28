<template>
  <Navbar></Navbar>
  <div class="container pt-1 pb-5">
    <router-view/>
  </div>
  <Footer></Footer>
</template>

<script>
import Footer from './components/FooterSegment'
import Navbar from './components/NavBarSegment'


export default {
  components: {
      Footer,
      Navbar
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
