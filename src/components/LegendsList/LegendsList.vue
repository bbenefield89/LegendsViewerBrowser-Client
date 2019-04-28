<template>
  <div>
    <h1>Legends List</h1>
    {{ logger(childComponent) }}
    <component :is="childComponent.component" :data="childComponent.data"></component>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'LegendsList'
})
class LegendsList extends Vue {

  @Prop() childComponent: any
  
  public logger(data: any): any {
    console.log(data)
  }
  
}

export default LegendsList
</script>

<style lang="scss" scoped>
</style>