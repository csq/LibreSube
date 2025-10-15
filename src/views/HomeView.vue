<template>
  <div class="home">
    <GreeterMessage msg="Bienvenido al portal LibreSUBE"/>
    <img class="img-responsive img-max" alt="logo" src="../assets/logo.svg">
  </div>

  <!-- cards -->
  <div class="row row-cols-1 row-cols-md-3 g-4 mb-4">
    <div class="col">
      <div class="card h-100">
        <router-link to="/charge-points" class="stretched-link"></router-link>
        <div class="card-body">
          <h5 class="card-title">Puntos de carga</h5>
          <p class="card-text">Localice los puntos de carga habilitados más cercanos.</p>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100">
        <router-link to="/tas" class="stretched-link"></router-link>
        <div class="card-body">
          <h5 class="card-title">Terminales automáticas SUBE</h5>
          <p class="card-text">Encuentre las terminales TAS más cercanas a usted.</p>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100">
        <router-link to="/data" class="stretched-link"></router-link>
        <div class="card-body">
          <h5 class="card-title">Gráficas del uso del sistema SUBE</h5>
          <p class="card-text">Visualice los datos referente al uso del sistema SUBE.</p>
        </div>
      </div>
    </div>
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
  max-width: 50rem;
  margin-top: 0rem;
  margin-bottom: 1rem;
}
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
  background: rgba(228, 238, 255, 0.774);
}
.card-title {
  font-size: large;
  font-weight: bold;
}
.card-text {
  text-align: justify;
}
</style>