<template>
  <div id="app">
    <!-- <HelloWorld msg="123123"/> -->
    <Prod></Prod>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';
import Prod from './components/Prod.vue';

@Component({
  components: {
    HelloWorld,
    Prod
  },
})
export default class App extends Vue {}
</script>

<style lang="less">
body,html{
  padding: 0;
  margin: 0;
}
</style>
