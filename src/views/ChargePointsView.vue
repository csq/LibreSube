<template>
  <div class="container">
    <h5>Centros de carga SUBE</h5>
    <div class="row pt-2">
      <div class="col-lg col-md-7 cold-sm">
        <div class="p-5 mb-4 border rounded-3" id="mapContainer"></div>
      </div>
      <div class="col-lg-4 col-sm">
        <div class="card">
          <div class="card-header">
            <b>Puntos de carga SUBE</b>
          </div>
          <div class="card-body">
            Son lugares habilitados donde podes cargar tu Tarjeta SUBE en forma presencial, estos puntos de carga se encuentran distribuidos por todo el país.
            <br><br>
            <strong>Tipos de puntos de carga:</strong>
            <ul>
              <li>Kioscos</li>
              <li>Locutorios</li>
              <li>Sucursales del Correo Argentino</li>
              <li>Terminales de Autoservicio SUBE</li>
              <li>Centros de Atención SUBE en distintos puntos del Área Metropolitana de Buenos Aires</li>
              <li>Agencias de Lotería Nacionales y Provinciales que tengan habilitado el servicio de recarga de SUBE</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import L from "leaflet";
import { MarkerClusterGroup } from 'leaflet.markercluster';
import 'leaflet.markercluster/dist/MarkerCluster.css';
import 'leaflet.markercluster/dist/MarkerCluster.Default.css';

import dataset from "@/datasets/Puntos de carga SUBE/sube_red_de_carga_activa_2019-10-01.geojson";
  
var geojsonMarkerOptions = {
    radius: 8,
    color: "#0378A6",
    weight: 1,
    opacity: 1,
    fillOpacity: 0.8
};
  
export default {
  name: "ChargePointsView",
  data() {
    return{
      center: [-42, -65] // Arg
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

      // Contendra al conjunto de marcadores
      var markers = new MarkerClusterGroup();
      
      L.geoJson(dataset, {
        pointToLayer: function (feature) {
          
          // Obtener latitud y longitud del archivo geojson
          var coords = [feature.properties.Longitud, feature.properties.Latitud]
          var latlng = L.GeoJSON.coordsToLatLng(coords);

          // Cada marcador es un circulo con su propia lat y lng 
          var marker = L.circleMarker(latlng, geojsonMarkerOptions);
          
          // Define el formato del popup
          marker.bindPopup(
            '<b><center>' + feature.properties[ 'Ubicaci�' ] + '</center></b>' + '<br>'+
            '<b>Dirección: </b>' + feature.properties[ 'Direcci�' ] + '<br>'+
            '<b>Localidad: </b>' + feature.properties.Localidad + '<br>'+
            '<b>Tipo: </b>' + feature.properties[ 'Tipo Ubica' ]);
          
          // Agrega cada marcador al conjunto de marcadores
          markers.addLayers(marker);
        }
      })
      
      // Agrega los marcadores en el mapa
      mapDiv.addLayer(markers);
    },
  },

  mounted() {
    this.setupLeafletMap();
  },
};
</script>
  
<style scoped>
.container {
  margin-top: 20px
}
#mapContainer {
  height: 550px;
}
ul {
  text-align: left;
}
.card-body {
  text-align: justify;
}
</style>