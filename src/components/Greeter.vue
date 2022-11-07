<template>
  <div class="message">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'GreeterMessage',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  margin: 2rem 0 0;
}
</style>
