<template>
  <div class="container">
    <div class="row">
      <h1 class="border-bottom border-dark mb-3 pb-1">LibreSUBE</h1>
      <p class="text-start">
        <b>LibreSUBE</b> es una aplicación de página única (Single-page application)
        que reúne y muestra información del Sistema Único de Boleto Electrónico (SUBE)
        de la República Argentina (puntos de carga, terminales de autoservicio,
        información de uso). Toda la información visualizada en esta aplicación se basan
        en datos generados por el sistema
        <a href="https://www.argentina.gob.ar/SUBE" target="_blank" class="text-decoration-none">SUBE</a>.
      </p>
      <h2 class="border-bottom border-dark mb-3 pt-3">Datasets utilizados</h2>
      <ul class="list">
        <li>
          <a
            href="https://datos.transporte.gob.ar/dataset/puntos-carga-sube" target="_blank"
            class="text-decoration-none">Puntos de carga</a
          >
        </li>
        <li>
          <a href="https://datos.transporte.gob.ar/dataset/terminales-automaticas-sube" target="_blank"
          class="text-decoration-none">Terminales Automáticas</a
          >
        </li>
        <li>
          <a href="https://www.datos.gob.ar/dataset/transporte-sube---cantidad-transacciones-usos-por-fecha" target="_blank"
          class="text-decoration-none">Cantidad de transacciones (usos) por fecha</a
          >
        </li>
        <li>
          <a href="https://www.datos.gob.ar/dataset/transporte-sube---cantidad-tarjetas-usuarios-por-dia" target="_blank"
          class="text-decoration-none">Cantidad de tarjetas (usuarios) por día</a
          >
        </li>
        <li>
          <a href="https://www.datos.gob.ar/dataset/transporte-operaciones-sube-por-mes-rmba" target="_blank"
          class="text-decoration-none">Operaciones de SUBE por mes en RMBA</a
          >
        </li>
      </ul>
      <h2 class="border-bottom border-dark mb-3 pt-3">
        Tecnologías empleadas
      </h2>
      <ul class="list">
        <li>Vue.js</li>
        <li>Vue-router</li>
        <li>Vue-ChartJS</li>
        <li>Leaflet</li>
        <li>Bootstrap</li>
      </ul>
      <h2 class="border-bottom border-dark mb-3 pt-3">Aviso legal</h2>
      <p class="text-start">
        NO GARANTIZAMOS LA EXACTITUD DE LOS DATOS. POR FAVOR UTILÍCELO COMO VISUAL
        DE AYUDA ÚNICAMENTE, Y NO BASE NINGUNA DECISIÓN DE CUALQUIER ÍNDOLE BASADA EN
        LOS DATOS PROPORCIONADOS EN LAS GRÁFICAS O MAPAS DE ESTA PÁGINA.<br/><br/>
        Tenga presente que la recopilación y actualización de los datos fuentes
        corren en responsabilidad de su originador. Por tal motivo los datos presentados
        podrían no estar actualizados a la fecha de consulta.
      </p>
    </div>
  </div>
</template>

<style>
.container {
  margin-top: 2rem;
}
ul.list li
{
 text-align: left;
 margin-left: 45%;
}
</style>