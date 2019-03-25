<template>
  <div>
    <h2>Underground Regions</h2>
    <ul>
      <li v-bind:key="underground_region.id[0]" v-for="underground_region in underground_regions">
        <p>{{ underground_region.id[0] }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'UndergroundRegions'
})
class UndergroundRegions extends Vue {
  @Prop() public underground_regions!: object[]
}

export default UndergroundRegions
</script>

<style lang="scss" scoped>
</style>