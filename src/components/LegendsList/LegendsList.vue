<template>
  <div>
    <h2>{{ listTitle }}</h2>
    
    <ul>
      <li v-bind:key="item.id[0]" v-for="item of list">
        <span v-if="item.description">{{ item.description[0] }}</span>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'LegendsList'
})
class LegendsList extends Vue {
  @Prop() public listTitle!: string
  @Prop() public list!: any
}

export default LegendsList
</script>

<style lang="scss" scoped>
</style>