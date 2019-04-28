<template>
  <li>
    <h3>
      {{ title }}
    </h3>

    <!-- IF -->
    <!-- <ul v-if="title.toLowerCase() === 'skills'"> -->
    <ul v-if="hfData[0].constructor.name === 'Object'">
      <li v-for="(data, idx) in hfData" :key="idx">
        <p v-for="val of data" :key="val[0]">
          {{ val[0] }}
        </p>
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
  
  public debug() {
    debugger
  }

  public getObjectEntries(obj: object): Array<any[]> {
    return Object.entries(obj)
  }
  
  public logger(data: any): void {
    console.log(data)
  }
}

export default HistoricalFigureDataItem
</script>

<style lang="scss" scoped>

</style>
