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
            Son lugares habilitados donde podés cargar tu Tarjeta SUBE en forma presencial, estos puntos de carga se encuentran distribuidos por todo el país.
            <br><br>
            <strong>Tipos de puntos de carga:</strong>
            <ul>
              <li>Kioscos</li>
              <li>Locutorios</li>
              <li>Sucursales del Correo Argentino</li>
              <li>Terminales de Autoservicio SUBE</li>
              <li>Centros de Atención SUBE</li>
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
import 'leaflet-fullscreen/dist/Leaflet.fullscreen.js';
import 'leaflet-fullscreen/dist/leaflet.fullscreen.css';

import dataset from "@/datasets/Puntos de carga SUBE/sube_red_de_carga_activa_2019-10-01.geojson";

// Variable contendrá la instancia del mapa
var map;

var geojsonMarkerOptions = {
    radius: 8,
    color: "#0378A6",
    weight: 1,
    opacity: 1,
    fillOpacity: 0.8
};

export default {
  name: "TasView",
  data() {
    return{
      center: [-42, -65], // Arg
      minZoom: 4,
      maxZoom: 15
    }
  },
  
  methods: {
    setupLeafletMap: function (center, zoom) {
      map = L.map("mapContainer").setView(center, zoom);
      L.tileLayer(
        'https://wms.ign.gob.ar/geoserver/gwc/service/tms/1.0.0/capabaseargenmap@EPSG%3A3857@png/{z}/{x}/{-y}.png',
        {
          attribution:
          '<a href="http://leafletjs.com" title="A JS library for interactive maps">Leaflet</a> | <a href="http://www.ign.gob.ar/AreaServicios/Argenmap/IntroduccionV2" target="_blank">Instituto Geográfico Nacional</a> + <a href="http://www.osm.org/copyright" target="_blank">OpenStreetMap</a>',
       }
      ).addTo(map);

      // Agrega un nuevo control al mapa para funcion fullscreen
      map.addControl(new L.Control.Fullscreen());

      // Contendra al conjunto de marcadores
      var markers = new MarkerClusterGroup();
      
      L.geoJson(dataset, {
        pointToLayer: function (feature) {
          
          // Obtener latitud y longitud del archivo geojson
          var coords = [feature.properties.Longitud, feature.properties.Latitud]
          var latlng = L.GeoJSON.coordsToLatLng(coords);

          // Cada marcador es un circulo con su propia lat y lng 
          var marker = L.circleMarker(latlng, geojsonMarkerOptions);

          // Solo muestra el nro de calles/avenidas significativas
          var numero = ''
          if (feature.properties[ 'N�mero' ] != "0") {
            numero = feature.properties[ 'N�mero' ]
          }
          
          // Define el formato del popup
          marker.bindPopup(
            '<b><center>' + feature.properties[ 'Ubicaci�' ] + '</center></b>' + '<br>'+
            '<b>Dirección: </b>' + feature.properties[ 'Direcci�' ] + ' ' + numero + '<br>'+
            '<b>Localidad: </b>' + feature.properties.Localidad + '<br>'+
            '<b>Tipo: </b>' + feature.properties[ 'Tipo Ubica' ]);
          
          // Agrega cada marcador al conjunto de marcadores
          markers.addLayers(marker);
        }
      })
      
      // Agrega los marcadores en el mapa
      map.addLayer(markers);
    },
  },

  mounted() {
    this.setupLeafletMap(this.center, this.minZoom);
  },

  created() {
    const success = (position) => {
      // Obtener lat y lng
      this.center = [position.coords.latitude, position.coords.longitude];

      // Marcador en la posición geolocalizada
      var marker = new L.Marker(this.center);
      map.setView(this.center, this.maxZoom);
      marker.addTo(map);
      marker.bindPopup('<b>Ubicación <br> apróximada</b>');
    };

    const error = (err) => {
      //console.warn(`ERROR(${err.code}): ${err.message}`);
      if (err.code == 1) {
        // User denied geolocation
      } 
    };

    const options = {
      enableHighAccuracy: false,
      timeout: 5000,
      maximumAge: 0
    };

    // Esto abrirá una ventana emergente de permiso
    navigator.geolocation.getCurrentPosition(success, error, options);
  }
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