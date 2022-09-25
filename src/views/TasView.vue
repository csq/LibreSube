<template>
  <div class="tas">
    <div id="mapContainer"></div>
  </div>
</template>

<script>
import L from "leaflet";
import dataset from "@/datasets/Terminales Automáticas SUBE/sube_terminales_autoservicio_activas_2019-10-01.geojson";

var geojsonMarkerOptions = {
    radius: 8,
    fillColor: "#42b983",
    color: "#000",
    weight: 1,
    opacity: 1,
    fillOpacity: 0.8
};

export default {
  name: "TasView",
  data() {
    return{
      center: [-41, -60] // Arg
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
          maxZoom: 50,
       }
      ).addTo(mapDiv);

      L.geoJson(dataset, {
        pointToLayer: function (feature) {
          
          // Obtener latitud y longitud del archivo geojson
          var lat = feature.properties.Latitud
          var lng = feature.properties.Longitud

          var latlng = L.latLng(lat, lng);

          return L.circleMarker(latlng, geojsonMarkerOptions);
        },
        onEachFeature: function (feature, layer) {
          layer.bindPopup(feature.properties.Provincia);
        }
      }).addTo(mapDiv);
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