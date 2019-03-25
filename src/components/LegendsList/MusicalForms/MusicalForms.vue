<template>
  <div>
    <h2>Musical Forms</h2>
    <ul>
      <li v-bind:key="musical_form.id[0]" v-for="musical_form in musical_forms">
        <p>{{ musical_form.id[0] }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'MusicalForms'
})
class MusicalForms extends Vue {
  @Prop() public musical_forms!: object[]
}

export default MusicalForms
</script>

<style lang="scss" scoped>
</style>