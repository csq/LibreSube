<template>
  <h5>{{ BarChartTitle }}</h5>
  <Bar
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
    <button class="btn btn-secondary btn-sm dropdown-toggle" type="button" data-bs-toggle="dropdown"
      aria-expanded="false">
      Año
    </button>
    <ul class="dropdown-menu dropdown-menu-dark">
      <li><a class="dropdown-item selected" v-on:click="getData(2022)">2022</a></li>
      <li>
        <hr class="dropdown-divider">
      </li>
      <li><a class="dropdown-item" v-on:click="getData(2021)">2021</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2020)">2020</a></li>
    </ul>
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

import data from "@/datasets/Info SUBE/total-usuarios-por-dia.csv";

// Arrays con los datos del csv
var date = new Array();
var bus = new Array();
var subway = new Array();
var train = new Array();

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  props: {
    chartId: {
      type: String,
      default: 'bar-chart'
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
  data() {
    return {
      BarChartTitle: null,
      chartData: {
        labels: date,
        datasets: [ {
          label: 'Colectivo',
          backgroundColor: '#E46651',
          data: bus
        },
        {
          label: 'Tren',
          backgroundColor: '#41B883',
          data: train
        },
        {
          label: 'Subte',
          backgroundColor: '#006AFF',
          data: subway
        } ]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false
      }
    }
  },
  methods: {
    getData: function (year) {
      if ( this.chartData.datasets[0].data.length != 0) {
        this.chartData.labels.length = 0;
        this.chartData.datasets[0].data.length = 0;
        this.chartData.datasets[1].data.length = 0;
        this.chartData.datasets[2].data.length = 0;
      }

      const regex = new RegExp(year+'-*');
      var index = 0;

      for (let i = 0; i < data.length; i++) {
        if (regex.test(data[i].indice_tiempo)) {
          this.chartData.labels[index] = data[i].indice_tiempo;
          this.chartData.datasets[0].data[index] = data[i].colectivo;
          this.chartData.datasets[1].data[index] = data[i].subte;
          this.chartData.datasets[2].data[index] = data[i].tren;
          index++;
        }
      }
      this.BarChartTitle = 'Usuarios por día en el año ' + year;
    }
  },
  created: function() {
    this.getData('2022');
  }
}           
</script>