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
</template>
  
<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

import data from "@/datasets/Info SUBE/total-usuarios-por-dia.csv";

var date = new Array();
var bus = new Array();
var subway = new Array();
var train = new Array();

var año = '2022'

const regex = new RegExp(año+'-*');

for (let i = 0; i < data.length; i++) {

  if (regex.test(data[i].indice_tiempo)) {
    date.push(data[i].indice_tiempo)
    bus.push(data[i].colectivo)
    subway.push(data[i].subte)
    train.push(data[i].tren)
  }
}

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
      BarChartTitle: 'Usuarios por día',
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
  }
}           
</script>