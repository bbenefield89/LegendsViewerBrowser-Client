<template>
  <div>
    <h2>Poetic Forms</h2>
    <ul>
      <li v-bind:key="poetic_form.id[0]" v-for="poetic_form in poetic_forms">
        <p>{{ poetic_form.id[0] }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'PoeticForms'
})
class PoeticForms extends Vue {
  @Prop() public poetic_forms!: object[]
}

export default PoeticForms
</script>

<style lang="scss" scoped>
</style>