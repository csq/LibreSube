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
            href="https://datos.transporte.gob.ar/dataset/puntos-carga-sube/archivo/7c90f2ec-af99-4e07-99ae-1ab3e8e1a26d" target="_blank"
            class="text-decoration-none">Puntos de carga
          </a>
          <p>Último cambio 15 de junio de 2022</p>
        </li>
        <li>
          <a
            href="https://datos.transporte.gob.ar/dataset/terminales-automaticas-sube/archivo/e2a67874-0b8b-485e-bace-a8e3a4cf86d1" target="_blank"
            class="text-decoration-none">Terminales Automáticas
          </a>
          <p>Último cambio 15 de junio de 2022</p>
        </li>
        <li>
          <a
            href="https://www.datos.gob.ar/dataset/transporte-sube---cantidad-tarjetas-usuarios-por-dia/archivo/transporte_3511fdd6-2c23-4069-8524-c66191becd06" target="_blank" 
            class="text-decoration-none">Cantidad de tarjetas (usuarios) por día
          </a>
          <p>Último cambio 23 de mayo de 2022</p>
        </li>
      </ul>
      </div>
      <div class="col">
        <ul class="list">
          <li>
          <a
            href="https://datos.transporte.gob.ar/dataset/sube-operaciones-viaje-por-mes-region-metropolitana-buenos-aires-agregado-por-mes/archivo/98cb974d-c519-426d-887e-74aafce389b1" target="_blank"
            class="text-decoration-none">Operaciones de viaje por Periodo
          </a>
          <p>Último cambio 15 de junio de 2022</p>
        </li>
        <li>
          <a
            href="https://datos.transporte.gob.ar/dataset/operaciones-sube-por-ano-rmba/archivo/8258c930-f011-4535-a4f9-651d1e2cae13" target="_blank"
            class="text-decoration-none">Cantidad de operaciones de viajes por año (detalle por modo)
          </a>
          <p>Último cambio 15 de junio de 2022</p>
        </li>
      </ul>
      </div>
      <p class="text-start pt-3">
        <b>Nota: </b>En ningún caso se realizaron modificaciones a los datasets, todos los cambios
        mencionados fueron realizados por el propietario de los mismos.
      </p>
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
  <div class="row">
    <div class="license">
      <a rel="license" href="http://creativecommons.org/licenses/by/4.0/" target="_blank"><img alt="Licencia Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />Esta obra está bajo una <a rel="license" href="http://creativecommons.org/licenses/by/4.0/" target="_blank">Licencia Creative Commons Atribución 4.0 Internacional</a>.
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