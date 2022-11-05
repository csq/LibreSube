<template>
  <div class="home">
    <GreeterMessage msg="Bienvenido al portal LibreSUBE"/>
    <img class="img-responsive img-max" alt="logo" src="../assets/logo.svg">
  </div>
</template>

<script>
// @ is an alias to /src
import GreeterMessage from '@/components/Greeter.vue'

export default {
  name: 'HomeView',
  components: {
    GreeterMessage
  }
}
</script>

<style scoped>
.img-max {
  max-width: 800px;
  margin-top: 2rem;
}
</style>