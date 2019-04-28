<template>
  <div>
    <h1>Categories</h1>

    <div class="categories_container">
      <button @click="renderChildComponent('HistoricalFigures')">Historical Figures</button>
      <button @click="renderChildComponent('DanceForms')">Dance Forms</button>
      <button @click="renderChildComponent('Entities')">Entities</button>
      <button @click="renderChildComponent('HistoricalEras')">Historical Eras</button>
      <button @click="renderChildComponent('HistoricalEventCollections')">Historical Event Collections</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

import HistoricalFigures from '@/components/LegendsList/HistoricalFigures/HistoricalFigures.vue'
import DanceForms from '@/components/LegendsList/DanceForms/DanceForms.vue'
import Entities from '@/components/LegendsList/Entities/Entities.vue'
import HistoricalEras from '@/components/LegendsList/HistoricalEras/HistoricalEras.vue'
import HistoricalEventCollections from '@/components/LegendsList/HistoricalEventCollections/HistoricalEventCollections.vue'

@Component({
  name: 'Categories'
})
class Categories extends Vue {

  public childComponents: { [key: string]: any } = { HistoricalFigures, DanceForms, Entities, HistoricalEras, HistoricalEventCollections }
  
  public renderChildComponent(component: string): void {
    this.$emit('render-child-component', this.childComponents[component], component)
  }
  
}

export default Categories
</script>

<style lang="scss" scoped>
</style>
