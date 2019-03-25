<template>
  <div>
    <h2>Historical Figures</h2>
    <ul>
      <li v-bind:key="historical_figure.id[0]" v-for="historical_figure in historical_figures">
        <p>{{ historical_figure.id[0] }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'HistoricalFigures'
})
class HistoricalFigures extends Vue {
  @Prop() public historical_figures!: object[]
}

export default HistoricalFigures
</script>

<style lang="scss" scoped>
</style>