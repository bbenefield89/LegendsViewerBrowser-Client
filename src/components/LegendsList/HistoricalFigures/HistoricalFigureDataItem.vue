<template>
  <li>
    <h3>
      {{ title }}
    </h3>

    <!-- IF -->
    <ul v-if="hfData[0].constructor.name === 'Object'">
      <li v-for="(data, idx) in hfData" :key="idx">
        <!-- IF -->
        <template v-if="title === 'Entity Link'">
          <ul v-for="val in data" :key="val[0]">
            <!-- IF -->
            <li v-if="Number(val[0]) >= 0">
              <p>Entity ID: {{ val[0] }}</p>
              <p>Entity Name: {{ getEntityLinkName(val) }}</p>
            </li>
            <!-- ELSE -->
            <li v-else>
              <p>{{ val[0] }}</p>
            </li>
          </ul>
        </template>
        <!-- ELSE -->
        <template v-else>
          <p v-for="val of data" :key="val[0]">
            {{ val[0] }}
          </p>
        </template>
      </li>
    </ul>
    <!-- ELSE -->
    <ul v-else>
      <li v-for="data in hfData " :key="data">
        <p>{{ data }}</p>
      </li>
    </ul>
  </li>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'HistoricalFigureDataItem'
})
class HistoricalFigureDataItem extends Vue {

  @Prop() public hfData!: any
  @Prop() public title!: string
  @Prop() public dfWorldHistory?: any
  
  public debug() {
    debugger
  }

  public getObjectEntries(obj: object): Array<any[]> {
    return Object.entries(obj)
  }

  public getEntityLinkName(current: any): any {
    const entityLinkName: any = this.dfWorldHistory.Entities.filter((entity: any) => {
      return entity.id[0] === current[0]
    })[0]
    return entityLinkName === undefined ? 'UNKNOWN' : entityLinkName.name ? entityLinkName.name[0] : 'UNKNOWN'
  }
  
  public logger(data: any): void {
    console.log(data)
  }
}

export default HistoricalFigureDataItem
</script>

<style lang="scss" scoped>

</style>
