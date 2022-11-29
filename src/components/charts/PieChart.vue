<template>
  <h5>{{ PieChartTitle }}</h5>
  <Pie
    :chart-options="chartOptions"
    :chart-data="chartData"
    :chart-id="chartId"
    :dataset-id-key="datasetIdKey"
    :plugins="plugins"
    :css-classes="cssClasses"
    :styles="styles"
    :width="width"
    :height="height"
  />
  <div class="dropdown">
    <button class="btn btn-secondary btn-sm dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
      Año
    </button>
    <ul class="dropdown-menu dropdown-menu-dark">
      <li><a class="dropdown-item selected" v-on:click="getData(2019)">2019</a></li>
      <li><hr class="dropdown-divider"></li>
      <li><a class="dropdown-item" v-on:click="getData(2018)">2018</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2017)">2017</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2016)">2016</a></li>
    </ul>
  </div>
</template>
  
<script>
import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale } from 'chart.js'

import data from "@/datasets/Info SUBE/cancelaciones_ano_modo.csv";

// Arrays con los datos del csv
var bus = new Array();
var subway = new Array();
var train = new Array();

ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale)
  
export default {
  name: 'PieChart',
  components: { Pie },
  props: {
    chartId: {
      type: String,
      default: 'pie-chart'
    },
    datasetIdKey: {
      type: String,
      default: 'label'
    },
    width: {
      type: Number,
      default: 400
    },
    height: {
      type: Number,
      default: 400
    },
    cssClasses: {
      default: '',
      type: String
    },
    styles: {
      type: Object,
      default: () => {}
    },
    plugins: {
      type: Object,
      default: () => {}
    }
  },
  // Configuración PieChart
  data() {
    return {
      PieChartTitle: '',
      chartData: {
        labels: [ 'Colectivo', 'Tren', 'Subte' ],
        datasets: [ {
          backgroundColor: ['#E46651', '#41B883', '#006AFF'],
          data: [bus, train, subway]
        } ]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false
      }
    }
  },
  methods: {
    // Extrae los datos del csv y los almacena en arrays
    getData: function(year) {

      // Limpia los array
      if (bus.length != 0) {
        bus.length = 0;
        subway.length = 0;
        train.length = 0;
      }

      const regex = new RegExp(year);

      for (let i = 0; i < data.length; i++) {

        if (regex.test(data[i].anio)) {
          if (data[i].MODO == "COLECTIVO") {
            bus.push(data[i].TOTAL)
          }else if (data[i].MODO == "SUBTE") {
            subway.push(data[i].TOTAL)
          } else {
            train.push(data[i].TOTAL)
          }
        }

      }
      // Establece en título del chart según el año seleccionado
      this.PieChartTitle = 'Usuarios en '+year+' por modo de transporte en la Región Metropolitana de Buenos Aires';
      
      this.updateData();
    },
    // Actualiza los datos del chart para que se visualizen
    updateData: function() {
      this.chartData.datasets[0].data = [bus, train, subway];
    }
  },
  // Ejecuta la funcion getData al cargar la pagina
  created: function() {
    this.getData('2019');
  }
}
</script>