<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">

    <UploadLegendsForm @upload-legends-file="setDwarfFortressWorldData" />

    <div class="legends_data_container">
      <Categories @render-child-component="renderChildComponent" />
      <LegendsList :childComponent="childComponent" />
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

  public childComponent: any = { component: null, data: null }
  public dwarfFortressWorldData: any = {}

  public renderChildComponent(component: any, componentName: string): void {
    this.childComponent.component = component
    this.childComponent.data = this.dwarfFortressWorldData[componentName]
  }

  public setDwarfFortressWorldData(e: any): void {
    console.log(e)
    this.dwarfFortressWorldData = e
  }
  
}
</script>

<style lang="scss" scoped>
.legends_data_container {
  display: flex;
  justify-content: space-around;
}
</style>