<template>
  <div>
    <h2>Entity Populations</h2>
    <ul>
      <li v-bind:key="entity_population.id[0]" v-for="entity_population in entity_populations">
        {{ entity_population.id[0] }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'Entities'
})
class Entities extends Vue {
  @Prop() public entity_populations!: object[]
}

export default Entities
</script>

<style lang="scss" scoped>
</style>