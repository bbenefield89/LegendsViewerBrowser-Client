<template>
  <div>
    <h2>Historical Eras</h2>
    <ul>
      <li v-bind:key="historical_era.name[0]" v-for="historical_era in historical_eras">
        <p>Era: {{ historical_era.name[0] }}</p>
        <p>Year: {{ historical_era.start_year[0] }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'HistoricalEras'
})
class HistoricalEras extends Vue {
  @Prop() public historical_eras!: object[]
}

export default HistoricalEras
</script>

<style lang="scss" scoped>
</style>