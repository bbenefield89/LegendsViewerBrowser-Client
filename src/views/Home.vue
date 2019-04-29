<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">

    <UploadLegendsForm
      @upload-legends-file="setdfWorldHistory"
    />

    <div class="legends_data_container">
      <Categories
        @render-child-component="renderChildComponent"
        @render-child-component-data="renderChildComponentData"
        :dfWorldData="dfWorldHistory"
      />

      <LegendsList
        :childComponent="childComponent"
        :dfWorldHistory="dfWorldHistory"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

import Categories from '@/components/Categories/Categories.vue'
import LegendsList from '@/components/LegendsList/LegendsList.vue'
import UploadLegendsForm from '@/components/UploadLegendsForm/UploadLegendsForm.vue';

@Component({
  components: {
    Categories,
    LegendsList,
    UploadLegendsForm
  }
})
export default class Home extends Vue {

  public childComponent: { component: any, data: object[] } = { component: null, data: [] }
  public dfWorldHistory: object|any = {}

  public renderChildComponent(component: any): void {
    this.childComponent.component = component
  }

  public renderChildComponentData(childComponentData: object|any): void {
    this.childComponent.data = [childComponentData]
  }

  public setdfWorldHistory(e: any): void {
    console.log(e)
    this.dfWorldHistory = e
  }
  
}
</script>

<style lang="scss" scoped>
.legends_data_container {
  display: flex;
  justify-content: space-around;
}
</style>