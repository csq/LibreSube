  <template>
    <div class="dashboard">
      <div class="p-5 mb-4 bg-light border rounded-3">
        <div class="container-fluid">
          <h5>Usuarios por día</h5>
          <BarChart></BarChart>
        </div>
      </div>
      <div class="row align-items-md-stretch">
        <div class="col-md-6">
          <div class="h-100 p-5 bg-light border rounded-3">
            <h5>Usuarios anuales por modo de transporte</h5>
            <PieChart></PieChart>
          </div>
        </div>
        <div class="col-md-6">
          <div class="h-100 p-5 bg-light border rounded-3">
            <h5>Operaciones de viaje por mes de Región Metropolitana de Buenos Aires</h5>
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
.dashboard {
  margin-top: 2rem;
}
</style>