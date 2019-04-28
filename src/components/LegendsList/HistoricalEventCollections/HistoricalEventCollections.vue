<template>
  <div>
    <h2>Historical Event Collections</h2>
    <ul>
      <li v-bind:key="historical_event_collection.id[0]" v-for="historical_event_collection in data">
        <p>ID: {{ historical_event_collection.id[0] }}</p>
        <p v-if="historical_event_collection.hasOwnProperty('coords')">Coords: {{ historical_event_collection.coords[0] }}</p>
        <p v-if="historical_event_collection.hasOwnProperty('defending_enid')">Defending Ent ID: {{ historical_event_collection.defending_enid[0] }}</p>
        <p>Start Year: {{ historical_event_collection.start_year[0] }}</p>
        <p>End Year: {{ historical_event_collection.end_year[0] }}</p>
        <p>Ordinal: {{ historical_event_collection.ordinal[0] }}</p>
        <p v-if="historical_event_collection.hasOwnProperty('parent_eventcol')">Parent Event Col: {{ historical_event_collection.parent_eventcol[0] }}</p>
        <p v-if="historical_event_collection.hasOwnProperty('site_id')">Site ID: {{ historical_event_collection.site_id[0] }}</p>
        <p v-if="historical_event_collection.hasOwnProperty('subregion_id')">Subregion ID: {{ historical_event_collection.subregion_id[0] }}</p>
        <p>Type: {{ historical_event_collection.type[0] }}</p>
        <p v-if="historical_event_collection.hasOwnProperty('event')">Event: {{ historical_event_collection.event[0] }}</p>
        <p v-if="historical_event_collection.hasOwnProperty('feature_layer_id')">Feature Layer ID: {{ historical_event_collection.feature_layer_id[0] }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'HistoricalEventCollections'
})
class HistoricalEventCollections extends Vue {
  @Prop() public data!: any[]
}

export default HistoricalEventCollections
</script>

<style lang="scss" scoped>
</style>