<template>
  <div class="home">
    <GreeterMessage msg="Bienvenido al portal LibreSUBE"/>
    <img class="img-responsive img-max" alt="logo" src="../assets/logo.svg">
  </div>

  <!-- cards -->
  <div class="row row-cols-1 row-cols-md-3 g-4">
    <div class="col">
      <div class="card h-100">
        <img src="../assets/card_images/charge_img.png" class="card-img-top" alt="charge_img">
        <a href="/charge-points"></a>
        <div class="card-body">
          <h5 class="card-title">Puntos de carga</h5>
          <p class="card-text">Localice los puntos de carga habilitados más cercanos a usted.</p>
        </div>
        <div class="card-link">
          <a href="/charge-points" class="btn btn-link btn-block">Acceder</a>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100">
        <img src="../assets/card_images/tas_img.png" class="card-img-top" alt="tas_img">
        <div class="card-body">
          <h5 class="card-title">Terminales automáticas SUBE</h5>
          <p class="card-text">Encuentre las terminales TAS más cercanas.</p>
        </div>
        <div class="card-link">
          <a href="/tas" class="btn btn-link btn-block">Acceder</a>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100" style="height: 1rem;">
        <img src="../assets/card_images/chart_img.png" class="card-img-top" alt="chart_img">
        <div class="card-body">
          <h5 class="card-title">Gráficas del uso del sistema SUBE</h5>
          <p class="card-text">Visualice los datos referente al uso del sistema SUBE.</p>
        </div>
        <div class="card-link">
          <a href="/data" class="btn btn-link btn-block">Acceder</a>
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
.card-title {
  font-size: large;
  font-weight: bold;
}
.card-text {
  text-align: start;
}
.card-link {
  border-top: 1px solid #D4D4D4;
  background-color: whitesmoke;
  border-bottom-right-radius: 5px;
  border-bottom-left-radius: 5px;
}
.card-link a {
  text-decoration: none !important;
  padding: 10px;
  padding-bottom: 5px;
  font-weight: 600;
  text-transform: uppercase;
}
</style>