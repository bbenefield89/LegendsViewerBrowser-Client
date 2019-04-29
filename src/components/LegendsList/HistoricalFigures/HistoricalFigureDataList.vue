<template>
  <ul>
    <HistoricalFigureDataItem
      title="ID"
      :hfData="historicalFigure.id"
    />

    <HistoricalFigureDataItem
      title="Name"
      :hfData="historicalFigure.name"
    />

    <HistoricalFigureDataItem
      v-if="historicalFigure.hasOwnProperty('race')"
      title="Race"
      :hfData="historicalFigure.race"
    />

    <HistoricalFigureDataItem
      v-if="historicalFigure.hasOwnProperty('caste')"
      title="Caste"
      :hfData="historicalFigure.caste"
    />

    <HistoricalFigureDataItem
      title="Birth Year"
      :hfData="historicalFigure.birth_year"
    />

    <HistoricalFigureDataItem
      title="Death Year"
      :hfData="historicalFigure.death_year[0] === '-1' ? ['Not Dead'] : historicalFigure.death_year"
    />

    <HistoricalFigureDataItem
      v-if="historicalFigure.hasOwnProperty('hf_skill')"
      title="Skills"
      :hfData="historicalFigure.hf_skill"
    />

    <HistoricalFigureDataItem
      v-if="historicalFigure.hasOwnProperty('associated_type')"
      title="Profession"
      :hfData="historicalFigure.associated_type"
    />

    <HistoricalFigureDataItem
      v-if="historicalFigure.hasOwnProperty('sphere')"
      title="Deity Sphere Types"
      :hfData="historicalFigure.sphere"
    />

    <HistoricalFigureDataItem
      v-if="historicalFigure.hasOwnProperty('entity_link')"
      title="Entity Link"
      :hfData="historicalFigure.entity_link"
      :dfWorldHistory="dfWorldHistory"
    />
  </ul>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

import HistoricalFigureDataItem from './HistoricalFigureDataItem.vue'

@Component({
  name: 'HistoricalFigureDataList',
  components: { HistoricalFigureDataItem }
})
class HistoricalFigureDataList extends Vue {

  @Prop() public logger!: Function
  @Prop() public historicalFigure!: any[]
  @Prop() public dfWorldHistory!: any

  public debug(): void {
    debugger
  }
  
}

export default HistoricalFigureDataList
</script>


<style lang="scss" scoped>

</style>

