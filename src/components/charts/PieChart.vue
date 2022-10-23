<template>
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
</template>
  
<script>
import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale } from 'chart.js'

import data from "@/datasets/Info SUBE/cancelaciones_ano_modo.csv";

var bus = new Array();
var subway = new Array();
var train = new Array();

var año = '2019'

const regex = new RegExp(año);

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
  data() {
    return {
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
  }
}
</script>