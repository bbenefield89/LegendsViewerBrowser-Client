<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
    <UploadLegendsForm/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import UploadLegendsForm from '@/components/UploadLegendsForm/UploadLegendsForm.vue';

@Component({
  components: {
    UploadLegendsForm,
  },
})
export default class Home extends Vue {}
</script>
