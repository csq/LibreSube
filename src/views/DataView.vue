<template>
  <div class="dashboard">
    <div class="p-4 pt-4 mb-4 bg-light border rounded-3">
      <div class="container-fluid">
        <BarChart></BarChart>
      </div>
    </div>
    <div class="row align-items-md-stretch">
      <div class="col-md-6 mb-4">
        <div class="h-100 p-4 bg-light border rounded-3">
          <PieChart></PieChart>
        </div>
      </div>
      <div class="col-md-6 mb-4">
        <div class="h-100 p-4 pt-4 bg-light border rounded-3">
          <LineChart></LineChart>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BarChart from '/src/components/charts/BarChart'
import PieChart from '/src/components/charts/PieChart'
import LineChart from '/src/components/charts/LineChart'

export default {
  name: 'App',
  components: { BarChart, PieChart, LineChart }
}
</script>

<style>
.dashboard,
.dropdown {
  margin-top: 2rem;
}
</style>