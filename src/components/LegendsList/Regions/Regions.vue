<template>
  <div>
    <h2>Regions</h2>
    <ul>
      <li v-bind:key="region.id[0]" v-for="region in regions">
        <p>{{ region.id[0] }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'Regions'
})
class Regions extends Vue {
  @Prop() public regions!: object[]
}

export default Regions
</script>

<style lang="scss" scoped>
</style>