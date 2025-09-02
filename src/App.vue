<template>
  <div class="app-container">
    <Navbar></Navbar>
    <div class="content-wrapper">
      <div class="container pt-1 pb-5">
        <router-view/>
      </div>
    </div>
    <Footer></Footer>
  </div>
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
html, body {
  height: 100%;
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.content-wrapper {
  flex: 1;
}
</style>
