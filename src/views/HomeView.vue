<template>
  <div class="home">
    <GreeterMessage msg="Bienvenido al portal LibreSUBE"/>
    <img alt="logo" src="../assets/logo.svg" width=600 height=500>
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
