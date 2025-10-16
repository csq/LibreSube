<template>
  <h5>{{ LineChartTitle }}</h5>
  <Line
    :data="chartData"
    :options="chartOptions"
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
      aria-expanded="false">{{ LineChartYear }}
    </button>
    <ul class="dropdown-menu dropdown-menu-dark">
      <li><a class="dropdown-item selected" v-on:click="getData(2019)">2019</a></li>
      <li>
        <hr class="dropdown-divider">
      </li>
      <li><a class="dropdown-item" v-on:click="getData(2018)">2018</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2017)">2017</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2016)">2016</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2015)">2015</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2014)">2014</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2013)">2013</a></li>
    </ul>
  </div>
</template>
  
<script>
import { Line } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, LineElement, LinearScale, PointElement, CategoryScale } from 'chart.js'

import data from "@/datasets/Info SUBE/operaciones-de-viaje-por-periodo.csv";

var mes = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio',
  'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre']

var operaciones_por_mes = new Array();

ChartJS.register(Title, Tooltip, Legend, LineElement, LinearScale, PointElement, CategoryScale)

export default {
  name: 'LineChart',
  components: { Line },
  props: {
    chartId: {
      type: String,
      default: 'line-chart'
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
      default: () => { }
    },
    plugins: {
      type: Object,
      default: () => { }
    }
  },
  data() {
    return {
      LineChartTitle: 'Operaciones de viaje en 2019 por mes en la Región Metropolitana de Buenos Aires',
      LineChartYear: '2019',
      chartData: {
        labels: mes,
        datasets: [{
          label: 'Operaciones',
          backgroundColor: '#f87979',
          data: operaciones_por_mes
        }]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: true,
        scales: {
          x: {
            type: 'category',
            title: {
              display: false,
              text: 'Meses',
            },
          },
          y: {
            type: 'linear',
            title: {
              display: true,
              text: 'Operaciones (Millones)',
            },
            ticks: {
              callback: function(value) {
                return (value / 1000000) + 'M';
              },
            },
          },
        },
      }
    }
  },
  methods: {
    getData: function (year) {
      var datasets = this.chartData.datasets;

      // Limpia el array
      datasets[0].data.length = 0;

      const regex = new RegExp(year);
      var month_index = 1;

      for (let i = 0; i < data.length; i++) {
        if (regex.test(data[i].PERIODO)) {
          operaciones_por_mes[month_index-1] = parseInt(data[i][" Suma de CANTIDAD "].split('.').join(''))
          month_index++;
        }
      }

      this.LineChartYear = year;
      this.LineChartTitle = `Operaciones de viaje en ${year} por mes en la Región Metropolitana de Buenos Aires`;
    }
  },
  created: function () {
    this.getData(2019);
  }
}
</script>