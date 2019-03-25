<template>
  <div>
    <h2>Historical Events</h2>
    <ul>
      <li v-bind:key="historical_event.id[0]" v-for="historical_event in historical_events">
        <p>{{ historical_event.id[0] }}</p>
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
  @Prop() public historical_events!: object[]
}

export default HistoricalEvents
</script>

<style lang="scss" scoped>
</style>