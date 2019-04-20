<template>
  <div>
    <h2>Historical Figures</h2>
    <ul>
      <li class="border" v-bind:key="historical_figure.id[0]" v-for="historical_figure in historical_figures">
        <p>ID: {{ historical_figure.id[0] }}</p>

        <p>Name: {{ historical_figure.name[0] }}</p>
        
        <p v-if="historical_figure.hasOwnProperty('race')">Race: {{ historical_figure.race[0] }}</p>
        
        <p v-if="historical_figure.hasOwnProperty('caste')">Caste/Gender: {{ historical_figure.caste[0] }}</p>
        
        <p>Year of Birth: {{ historical_figure.birth_year[0] }} (Appeared in {{ historical_figure.appeared[0] }})</p>
        
        <p>Year of Death: {{ historical_figure.death_year[0] }}</p>
        
        <div class="border">
          <h2>Skills</h2>
          <p v-bind:key="skill.skill[0]" v-for="skill in historical_figure.hf_skill">
            <span>{{ skill.skill[0] }}: {{ skill.total_ip[0] }}</span>
          </p>
        </div>
        
        <p v-if="historical_figure.hasOwnProperty('associated_type')">
          Profession: {{ historical_figure.associated_type[0] }}
        </p>
        
        <div v-if="historical_figure.hasOwnProperty('sphere')" class="border">
          <p v-bind:key="sphere" v-for="sphere in historical_figure.sphere">
            Deity Sphere Type: {{ sphere }}
          </p>
        </div>

        <div class="border" v-if="historical_figure.hasOwnProperty('entity_link')">
          <p v-bind:key="link.entity_id[0] + link.link_type[0]" v-for="link in historical_figure.entity_link">
            Entity ID: {{ link.entity_id[0] }}
            <br />
            Link Type: {{ link.link_type[0] }}
            <br />
            <span v-if="link.hasOwnProperty('link_strength')">
              Link Strength: {{ link.link_strength[0] }}
            </span>
          </p>
        </div>

        <p v-if="historical_figure.hasOwnProperty('site_link')">
          Site ID: {{ historical_figure.site_link[0].site_id[0] }}
          <br />
          Site Type: {{ historical_figure.site_link[0].link_type[0] }}
        </p>

        <div class="border" v-if="historical_figure.hasOwnProperty('hf_link')">
          <p v-bind:key="link.hfid[0]" v-for="link in historical_figure.hf_link">
            HF ID: {{ link.hfid[0] }}
            <br />
            Link Type: {{ link.link_type[0] }}
          </p>
        </div>

        <div class="border" v-if="historical_figure.hasOwnProperty('entity_position_link')">
          <p v-bind:key="link.entity_id[0]" v-for="link in historical_figure.entity_position_link">
            Entity ID: {{ link.entity_id[0] }}
            <br />
            Position Profile ID: {{ link.position_profile_id[0] }}
            <br />
            Start Year: {{ link.start_year[0] }}
          </p>
        </div>

        <p v-if="historical_figure.hasOwnProperty('goal')">
          Life Goal: {{ historical_figure.goal[0] }}
        </p>

        <p v-if="historical_figure.hasOwnProperty('ent_pop_id')">
          Ent Pop ID: {{ historical_figure.ent_pop_id[0] }}
        </p>

        <p v-if="historical_figure.hasOwnProperty('journey_pet')">
          Journey Pet: {{ historical_figure.journey_pet[0] }}
        </p>

        <!--
          journey_pet
        -->
        <br /><br />
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'HistoricalFigures'
})
class HistoricalFigures extends Vue {
  @Prop() public historical_figures!: object[]

  public skills: Set<any> = new Set()

  public logger(data: any): void {
    console.log(data)
  }
}

export default HistoricalFigures
</script>

<style lang="scss" scoped>
  .border {
    border: 1px solid #000;
  }
</style>