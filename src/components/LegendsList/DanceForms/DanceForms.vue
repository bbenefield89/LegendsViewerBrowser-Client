<template>
  <div>
    <h2>Dance Forms</h2>
    <ul>
      <li v-bind:key="dance_form.id[0]" v-for="dance_form in data">
        {{ dance_form.description[0] }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'DanceForms'
})
class DanceForms extends Vue {
  @Prop() public data!: object[]
}

export default DanceForms
</script>

<style lang="scss" scoped>
</style>