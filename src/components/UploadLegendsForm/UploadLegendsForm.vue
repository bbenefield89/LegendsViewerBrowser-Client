<template>
  <div>
    <form v-on:submit="uploadLegendsXmlFile">
      <label for="upload_legends_input" />
      <input name="upload_legends_input" type="file" />
      <input type="submit" />
    </form>

    <DanceForms :dance_forms="dance_forms" />
    <Entities :entities="entities" />
    <EntityPopulations :entity_populations="entity_populations" />
    <HistoricalEras :historical_eras="historical_eras" />
    <HistoricalEventCollections :historical_event_collections="historical_event_collections" />
    <HistoricalEvents :historical_events="historical_events" />
    <HistoricalFigures :historical_figures="historical_figures" />
    <MusicalForms :musical_forms="musical_forms" />
    <PoeticForms :poetic_forms="poetic_forms" />
    <Regions :regions="regions" />
    <Sites :sites="sites" />
    <UndergroundRegions :underground_regions="underground_regions" />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'
import { parseString } from 'xml2js'

import LegendsList from '../LegendsList/LegendsList.vue'
import DanceForms from '../LegendsList/DanceForms/DanceForms.vue'
import Entities from '../LegendsList/Entities/Entities.vue'
import EntityPopulations from '../LegendsList/EntityPopulations/EntityPopulations.vue'
import HistoricalEras from '../LegendsList/HistoricalEras/HistoricalEras.vue'
import HistoricalEventCollections from '../LegendsList/HistoricalEventCollections/HistoricalEventCollections.vue'
import HistoricalEvents from '../LegendsList/HistoricalEvents/HistoricalEvents.vue'
import HistoricalFigures from '../LegendsList/HistoricalFigures/HistoricalFigures.vue'
import MusicalForms from '../LegendsList/MusicalForms/MusicalForms.vue'
import PoeticForms from '../LegendsList/PoeticForms/PoeticForms.vue'
import Regions from '../LegendsList/Regions/Regions.vue'
import Sites from '../LegendsList/Sites/Sites.vue'
import UndergroundRegions from '../LegendsList/UndergroundRegions/UndergroundRegions.vue'

@Component({
  name: 'UploadLegendsForm',
  components: { LegendsList, DanceForms, Entities, EntityPopulations, HistoricalEras, HistoricalEventCollections, HistoricalEvents, HistoricalFigures, MusicalForms, PoeticForms, Regions, Sites, UndergroundRegions }
})
export default class UploadLegendsForm extends Vue {
  public dance_forms: object[] = []
  public entities: object[] = []
  public entity_populations: object[] = []
  public historical_eras: object[] = []
  public historical_event_collections: object[] = []
  public historical_events: object[] = []
  public historical_figures: object[] = []
  public musical_forms: object[] = []
  public poetic_forms: object[] = []
  public regions: object[] = []
  public sites: object[] = []
  public underground_regions: object[] = []


  public uploadLegendsXmlFile(e: any): void {
    e.preventDefault()
    const fileInput: any = document.querySelector('[type="file"]')
    const legendsXmlFile: any = fileInput.files[0]
    const fileReader: any = new FileReader()
    fileReader.onerror = (err: any): void => console.log('error', err)
    fileReader.onprogress = (res: any): any => null
    fileReader.onload = (res: any): void => {
      parseString(res.srcElement.result, (err: any, result: any) => {
        console.log(result.df_world)
        this.dance_forms = result.df_world.dance_forms[0].dance_form
        this.entities = result.df_world.entities[0].entity
        this.entity_populations = result.df_world.entity_populations[0].entity_population
        this.historical_eras = result.df_world.historical_eras[0].historical_era
        this.historical_event_collections = result.df_world.historical_event_collections[0].historical_event_collection
        this.historical_events = result.df_world.historical_events[0].historical_event
        this.historical_figures = result.df_world.historical_figures[0].historical_figure
        this.musical_forms = result.df_world.musical_forms[0].musical_form
        this.poetic_forms = result.df_world.poetic_forms[0].poetic_form
        this.regions = result.df_world.regions[0].region
        this.sites = result.df_world.sites[0].site
        this.underground_regions = result.df_world.underground_regions[0].underground_region
      })
    }
    fileReader.readAsText(legendsXmlFile)
  }

  public filterList(): any {
    console.log('Hello')
  }
}
</script>

<style>
ul {
  margin-bottom: 3rem;
}

li {
  margin-bottom: 1.5rem;
}
</style>
