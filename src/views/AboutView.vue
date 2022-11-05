<template>
  <div class="container">
    <div class="row">
      <h2 class="border-bottom border-dark mb-3 pb-1">LibreSUBE</h2>
      <p class="text-start">
        <b>LibreSUBE</b> es una aplicación de página única (Single-page application)
        que reúne y muestra información del Sistema Único de Boleto Electrónico <b>(SUBE)</b>
        de la República Argentina tales como la ubicación de los puntos de carga, terminales de autoservicio,
        e información de la utilización del sistema. Toda la información reunida y visualizada en esta aplicación se basan
        en datos primarios generados por el sistema
        <a href="https://www.argentina.gob.ar/SUBE" target="_blank" class="text-decoration-none">SUBE</a>.
      </p>
      <h3 class="border-bottom border-dark mb-3 pt-3">Datasets utilizados</h3>
      <div class="col">
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
      </ul>
      </div>
      <div class="col">
        <ul class="list">
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
      </div>
      <h3 class="border-bottom border-dark mb-3 pt-3">Aviso legal</h3>
      <p class="text-start">
        NO GARANTIZAMOS LA EXACTITUD DE LOS DATOS. POR FAVOR UTILÍCELO COMO VISUAL
        DE AYUDA ÚNICAMENTE, Y NO BASE NINGUNA DECISIÓN DE CUALQUIER ÍNDOLE BASADA EN
        LOS DATOS PROPORCIONADOS EN LAS GRÁFICAS O MAPAS DE ESTA PÁGINA.<br/><br/>
        Tenga presente que la recopilación y actualización de los datos fuentes
        corren en responsabilidad de su originador. Por tal motivo los datos presentados
        podrían no estar actualizados a la fecha de consulta.<br/><br/>
      </p>
    </div>
  </div>
</template>

<style scoped>
.container {
  margin-top: 2rem;
}
.list {
 text-align: left;
}
</style>