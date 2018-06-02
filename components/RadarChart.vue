<script>
import { Radar } from "vue-chartjs"
export default {
  extends: Radar,
  name: "Radar",
  props: ['data', 'options'],
  mounted () {
    this.renderChart(this.data, this.options)
  }
}
</script>

<style>

</style>
