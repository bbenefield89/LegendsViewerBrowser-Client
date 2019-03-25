<template>
  <div>
    <h2>Sites</h2>
    <ul>
      <li v-bind:key="site.id[0]" v-for="site in sites">
        <p>{{ site.id[0] }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'Sites'
})
class Sites extends Vue {
  @Prop() public sites!: object[]
}

export default Sites
</script>

<style lang="scss" scoped>
</style>