<template>
  <div class="categories_container">
    <h1>Categories</h1>

    <div class="categories_container__labels_container">
      <button @click="setSearchResults('HistoricalFigures')">Historical Figures</button>
      <!-- <button @click="setSearchResults('DanceForms')">Dance Forms</button>
      <button @click="setSearchResults('Entities')">Entities</button>
      <button @click="setSearchResults('HistoricalEras')">Historical Eras</button>
      <button @click="setSearchResults('HistoricalEventCollections')">Historical Event Collections</button>
      <button @click="setSearchResults('HistoricalEvents')">Historical Events</button> -->
    </div>

    <div class="categories_container__search_container">
      <ul>
        <li v-for="(searchResult, idx) of searchResults" :key="idx">
          <button @click="renderChildComponentData(searchResult)">{{ searchResult.name[0] }}</button>
        </li>
      </ul>
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
import HistoricalEvents from '@/components/LegendsList/HistoricalEvents/HistoricalEvents.vue'

@Component({
  name: 'Categories'
})
class Categories extends Vue {

  @Prop() dfWorldData!: any

  public childComponents: { [key: string]: any } = { HistoricalFigures, DanceForms, Entities, HistoricalEras, HistoricalEventCollections, HistoricalEvents }
  public searchResults: object[] = []
  
  public logger(data: any) {
    console.log(data)
  }
  
  public setSearchResults(searchFor: string): any {
    this.searchResults = this.dfWorldData[searchFor]
    this.$emit('render-child-component', this.childComponents[searchFor])
  }
  
  public renderChildComponentData(childComponentData: string): void {
    this.$emit('render-child-component-data', childComponentData)
  }
  
}

export default Categories
</script>

<style lang="scss" scoped>
</style>
