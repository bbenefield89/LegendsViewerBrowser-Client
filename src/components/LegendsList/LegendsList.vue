<template>
  <div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

import DanceForms from './DanceForms/DanceForms.vue'

@Component({
  name: 'LegendsList',
  components: { DanceForms }
})
class LegendsList extends Vue {
  @Prop() public listTitle!: any
  @Prop() public list!: any
  @Prop() public childComponent!: any
}

export default LegendsList
</script>

<style lang="scss" scoped>
</style>