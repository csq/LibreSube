<template>
  <form class="row input-bottom-margin-10 ng-pristine ng-valid" method="post">
    <div class="col-md-3 col-6 pt-2">
      <div class="form-group" data-ng-class="{'state-loading': getProvinces}" style="">
        <select class="form-select ng-pristine ng-untouched ng-valid ng-empty" data-ng-model="Filtro.Province" id="city" name="dllProvince" data-ng-options="Province as Province.Descripcion  for Province in Provinces" data-ng-change="ViewDataLocations()" aria-invalid="false"><option value="" disabled="" selected="selected" class="">Provincia</option><option label="BUENOS AIRES" value="object:4">BUENOS AIRES</option><option label="CABA" value="object:5">CABA</option><option label="CATAMARCA" value="object:6">CATAMARCA</option><option label="CHACO" value="object:7">CHACO</option><option label="CHUBUT" value="object:8">CHUBUT</option><option label="CÓRDOBA" value="object:9">CÓRDOBA</option><option label="CORRIENTES" value="object:10">CORRIENTES</option><option label="ENTRE RÍOS" value="object:11">ENTRE RÍOS</option><option label="FORMOSA" value="object:12">FORMOSA</option><option label="JUJUY" value="object:13">JUJUY</option><option label="LA PAMPA" value="object:14">LA PAMPA</option><option label="MENDOZA" value="object:15">MENDOZA</option><option label="MISIONES" value="object:16">MISIONES</option><option label="NEUQUÉN" value="object:17">NEUQUÉN</option><option label="RÍO NEGRO" value="object:18">RÍO NEGRO</option><option label="SAN JUAN" value="object:19">SAN JUAN</option><option label="SAN LUIS" value="object:20">SAN LUIS</option><option label="SANTA FE" value="object:21">SANTA FE</option><option label="TIERRA DEL FUEGO" value="object:22">TIERRA DEL FUEGO</option></select>
      </div>
    </div>
  </form>
  <div id="mapContainer"></div>
</template>

<script>
import L from "leaflet";
import dataset from "@/datasets/Puntos de carga SUBE/sube_red_de_carga_activa_2019-10-01.geojson";
  
var geojsonMarkerOptions = {
    radius: 8,
    fillColor: "#52c7ea",
    color: "#000",
    weight: 1,
    opacity: 1,
    fillOpacity: 0.8
};
  
export default {
  name: "ChargePointsView",
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
          layer.bindPopup(
          '<b><center>' + feature.properties[ 'Ubicaci�' ] + '</center></b>' + '<br>'+
          '<b>Dirección: </b>' + feature.properties[ 'Direcci�' ] + '<br>'+
          '<b>Localidad: </b>' + feature.properties.Localidad + '<br>'+
          '<b>Tipo: </b>' + feature.properties[ 'Tipo Ubica' ]);
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
.form-group {
  padding-bottom: 10px;
}

#mapContainer {
  height: 550px;
}
</style>