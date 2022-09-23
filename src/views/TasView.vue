<template>
  <div class="tas">
    <div id="mapContainer"></div>
  </div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";
//import dataset from "@/datasets/Terminales Automáticas SUBE/sube_terminales_autoservicio_activas_2019-10-01.geojson";

export default {
  name: "TasView",
  data() {
    return{
      center: [-41, -60]
    }
  },
  
  methods: {
    setupLeafletMap: function () {
      const mapDiv = L.map("mapContainer").setView(this.center, 4);
      L.tileLayer(
        'https://wms.ign.gob.ar/geoserver/gwc/service/tms/1.0.0/capabaseargenmap@EPSG%3A3857@png/{z}/{x}/{-y}.png',
        {
          attribution:
          '<a href="http://leafletjs.com" title="A JS library for interactive maps">Leaflet</a> | <a href="http://www.ign.gob.ar/AreaServicios/Argenmap/IntroduccionV2" target="_blank">Instituto Geográfico Nacional</a> + <a href="http://www.osm.org/copyright" target="_blank">OpenStreetMap</a>',
          minZoom: 3,
          maxZoom: 18,
       }
      ).addTo(mapDiv);
      //L.geoJSON(dataset).addTo(mapDiv);
    },
  },
  mounted() {
    this.setupLeafletMap();
  },
};
</script>

<style scoped>
#mapContainer {
  height: 550px;
}
</style>