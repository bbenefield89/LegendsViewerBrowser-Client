<template>
  <div>
    <h1>Legends List</h1>
    <component
      :is="childComponent.component"
      :data="childComponent.data"
      :dfWorldHistory="dfWorldHistory"
    />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'LegendsList'
})
class LegendsList extends Vue {

  @Prop() childComponent: object|any
  @Prop() dfWorldHistory: object|any
  
  public logger(data: any): any {
    console.log(data)
  }
  
}

export default LegendsList
</script>

<style lang="scss" scoped>
</style>