<template>
  <div id="app">
    <!-- <HelloWorld msg="123123"/> -->
    <Example></Example>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';
import Example from './components/Example.vue';

@Component({
  components: {
    HelloWorld,
    Example
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
