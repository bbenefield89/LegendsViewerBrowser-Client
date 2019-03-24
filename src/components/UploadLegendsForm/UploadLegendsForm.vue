<template>
  <div>
    <form v-on:submit="uploadLegendsXmlFile">
      <label for="upload_legends_input" />
      <input name="upload_legends_input" type="file" />
      <input type="submit" />
    </form>

    <div>
      <h2>Dance Forms</h2>
      <ul>
        <li v-bind:key="dance_form.id[0]" v-for="dance_form in dance_forms">
          {{ dance_form.description[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Entities</h2>
      <ul>
        <li v-bind:key="entity.id[0]" v-for="entity in entities">
          <span v-if="entity.name">{{ entity.name[0] }}</span>
          <span v-else>UNKNOWN ENTITY</span>
        </li>
      </ul>
    </div>

    <div>
      <h2>Entity Populations</h2>
      <ul>
        <li v-bind:key="entity_population.id[0]" v-for="entity_population in entity_populations">
          {{ entity_population.id[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Historical Eras</h2>
      <ul>
        <li v-bind:key="historical_era.name[0]" v-for="historical_era in historical_eras">
          {{ historical_era.name[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Historical Event Collections</h2>
      <ul>
        <li v-bind:key="historical_event_collection.id[0]" v-for="historical_event_collection in historical_event_collections">
          {{ historical_event_collection.id[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Historical Events</h2>
      <ul>
        <li v-bind:key="historical_event.id[0]" v-for="historical_event in historical_events">
          {{ historical_event.id[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Historical Figures</h2>
      <ul>
        <li v-bind:key="historical_figure.id[0]" v-for="historical_figure in historical_figures">
          {{ historical_figure.id[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Musical Forms</h2>
      <ul>
        <li v-bind:key="musical_form.id[0]" v-for="musical_form in musical_forms">
          {{ musical_form.id[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Poetic Forms</h2>
      <ul>
        <li v-bind:key="poetic_form.id[0]" v-for="poetic_form in poetic_forms">
          {{ poetic_form.id[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Regions</h2>
      <ul>
        <li v-bind:key="region.id[0]" v-for="region in regions">
          {{ region.id[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Sites</h2>
      <ul>
        <li v-bind:key="site.id[0]" v-for="site in sites">
          {{ site.id[0] }}
        </li>
      </ul>
    </div>

    <div>
      <h2>Underground Regions</h2>
      <ul>
        <li v-bind:key="underground_region.id[0]" v-for="underground_region in underground_regions">
          {{ underground_region.id[0] }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'
import { parseString } from 'xml2js'

import LegendsList from '../LegendsList/LegendsList.vue'

@Component
export default class UploadLegendsForm extends Vue {

  public dance_forms: any = []
  public entities: any = []
  public entity_populations: any = []
  public historical_eras: any = []
  public historical_event_collections: any = []
  public historical_events: any = []
  public historical_figures: any = []
  public musical_forms: any = []
  public poetic_forms: any = []
  public regions: any = []
  public sites: any = []
  public underground_regions: any = []

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
