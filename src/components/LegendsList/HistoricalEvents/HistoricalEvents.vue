<template>
  <div>
    <h2>Historical Events</h2>
    <ul>
      <li v-bind:key="historical_event.id[0]" v-for="historical_event in data">
        <p>ID: {{ historical_event.id[0] }}</p>
        <p v-if="historical_event.hasOwnProperty('coords')">Coords: {{ historical_event.coords[0] }}</p>
        <p v-if="historical_event.hasOwnProperty('feature_layer_id')">Feature Layer ID: {{ historical_event.feature_layer_id[0] }}</p>
        <p v-if="historical_event.hasOwnProperty('hfid')">Historical Figure ID: {{ historical_event.hfid[0] }}</p>
        <p v-if="historical_event.hasOwnProperty('hfid')">Historical Figure ID: {{ historical_event.hfid[0] }}</p>
        <p v-if="historical_event.hasOwnProperty('site_id')">Site ID: {{ historical_event.site_id[0] }}</p>
        <p v-if="historical_event.hasOwnProperty('state')">State: {{ historical_event.state[0] }}</p>
        <p v-if="historical_event.hasOwnProperty('subregion_id')">Subregion ID: {{ historical_event.subregion_id[0] }}</p>
        <p>Type: {{ historical_event.type[0] }}</p>
        <p>Year: {{ historical_event.year[0] }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'HistoricalEvents'
})
class HistoricalEvents extends Vue {
  @Prop() public data!: object[]
}

export default HistoricalEvents
</script>

<style lang="scss" scoped>
</style>