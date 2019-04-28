<template>
  <div>
    <h2>Entities</h2>
    <ul>
      <li v-bind:key="entity.id[0]" v-for="entity in data">
        <p>ID: {{ entity.id[0] }}</p>
        <!-- IF -->
        <p v-if="entity.name">Entity Name: {{ entity.name[0] }}</p>
        <!-- ELSE -->
        <p v-else>UNKNOWN ENTITY</p>
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
  @Prop() public data!: object[]
}

export default Entities
</script>

<style lang="scss" scoped>
</style>