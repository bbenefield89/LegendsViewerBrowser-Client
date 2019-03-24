<template>
  <div>
    <h2>Dance Forms</h2>
    <input type="text" />
    <ul>
      <li v-bind:key="item.id[0]" v-for="item in list">
        {{ item.description[0] }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component
export default class LegendsList extends Vue {
  @Prop() private list: any[] = []
}
</script>

<style lang="scss" scoped>
</style>