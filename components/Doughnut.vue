<script>
import { Doughnut } from "vue-chartjs"
export default {
  extends: Doughnut,
  name: "doughnut",
  props: ['data', 'options'],
  mounted () {
    this.renderChart(this.data, this.options)
  }
}
</script>

<style>

</style>
