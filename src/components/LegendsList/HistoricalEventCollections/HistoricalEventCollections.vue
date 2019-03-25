<template>
  <div>
    <h2>Historical Event Collections</h2>
    <ul>
      <li v-bind:key="historical_event_collection.id[0]" v-for="historical_event_collection in historical_event_collections">
        <p>{{ historical_event_collection.id[0] }}</p>
        <!-- <p>{{ historical_event_collection.coords[0] }}</p>
        <p>{{ historical_event_collection.defending_enid[0] }}</p>
        <p>{{ historical_event_collection.end_seconds72[0] }}</p>
        <p>{{ historical_event_collection.end_year[0] }}</p>
        <p>{{ historical_event_collection.ordinal[0] }}</p>
        <p>{{ historical_event_collection.parent_eventcol[0] }}</p>
        <p>{{ historical_event_collection.site_id[0] }}</p>
        <p>{{ historical_event_collection.start_seconds72[0] }}</p>
        <p>{{ historical_event_collection.start_year[0] }}</p>
        <p>{{ historical_event_collection.subregion_id[0] }}</p>
        <p>{{ historical_event_collection.type[0] }}</p>
        <p>{{ historical_event_collection.event[0] }}</p>
        <p>{{ historical_event_collection.feature_layer_id[0] }}</p> -->
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
  @Prop() public historical_event_collections!: any[]
}

export default HistoricalEventCollections
</script>

<style lang="scss" scoped>
</style>