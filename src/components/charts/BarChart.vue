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
      aria-expanded="false">{{ BarChartYear }}
    </button>
    <ul class="dropdown-menu dropdown-menu-dark">
      <li><a class="dropdown-item selected" v-on:click="getData(2025)">2025</a></li>
      <li>
        <hr class="dropdown-divider">
      </li>
      <li><a class="dropdown-item" v-on:click="getData(2024)">2024</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2023)">2023</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2022)">2022</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2021)">2021</a></li>
      <li><a class="dropdown-item" v-on:click="getData(2020)">2020</a></li>
    </ul>
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
import zoomPlugin from 'chartjs-plugin-zoom';

import data from "@/datasets/Info SUBE/total-usuarios-por-dia.csv";

// Arrays con los datos del csv
var date = new Array();
var bus = new Array();
var subway = new Array();
var train = new Array();

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale, zoomPlugin)

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
      BarChartTitle: 'Usuarios por dia 2025',
      BarChartYear: '2025',
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
        maintainAspectRatio: false,
        plugins: {
          zoom: {
            zoom: {
              wheel: {
                enabled: true,
                speed: 0.2
              },
              pinch: {
                enabled: true
              },
              drag: {
                enabled: true,
                backgroundColor: 'rgba(0, 103, 255, 0.20)',
                borderColor: 'rgba(18, 18, 18, 1)',
                borderWidth: 0.3,
                threshold: 2
              },
              mode: 'x'
            }
          }
        },
        scales: {
          x: {
            type: 'category',
            title: {
              display: false,
              text: 'Fecha',
            },
          },
          y: {
            type: 'linear',
            title: {
              display: true,
              text: 'Usuarios (Millones)',
            },
            ticks: {
              callback: function(value) {
                return value / 1000000 + 'M';
              }
            }
          }
        }
      }
    }
  },
  methods: {
    getData: function (year) {
      var datasets = this.chartData.datasets;
      var labels = this.chartData.labels;

      // Limpia los array
      labels.length = 0;
      for (let index = 0; index < 3; index++) {
        datasets[index].data.length = 0;
      }

      const regex = new RegExp(year+'-*');
      var index = 0;

      for (let i = 0; i < data.length; i++) {
        if (regex.test(data[i].indice_tiempo)) {
          labels[index] = this.convertDate(data[i].indice_tiempo);
          datasets[0].data[index] = data[i].colectivo;
          datasets[1].data[index] = data[i].tren;
          datasets[2].data[index] = data[i].subte;
          index++;
        }
      }
      this.BarChartYear = year;
      this.BarChartTitle = `Usuarios por día ${year}`;
    },
    convertDate: function (originalDate) {
      const [, month, day] = originalDate.split('-');
      return `${month}/${day}`;
    }
  },
  created: function() {
    this.getData('2025');
  }

}           
</script>