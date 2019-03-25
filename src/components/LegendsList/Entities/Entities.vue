<template>
  <div>
    <h2>Entities</h2>
    <ul>
      <li v-bind:key="entity.id[0]" v-for="entity in entities">
        <span v-if="entity.name">{{ entity.name[0] }}</span>
        <span v-else>UNKNOWN ENTITY</span>
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
  @Prop() public entities!: object[]
}

export default Entities
</script>

<style lang="scss" scoped>
</style>