<template>
  <div class="prod">
    <Tag v-model="tags">
      <div slot-scope="{ tags, removeTag, inputAttrs, inputEvents, addTag }">
        <div v-for="(tag, index) in tags" :key="index">
          <span>{{tag}}</span>
          <button @click="removeTag(tag)">&times;</button>
        </div>
        <input type="text" v-bind="inputAttrs" v-on="inputEvents" placeholder="Add tag">
        <button @click="addTag">add</button>
      </div>
    </Tag>
    <p>{{str}}</p>
    <Throttling v-model="str" :delay="500">
      <input slot-scope="{ inputAttrs, inputEvents }" type="text" v-bind="inputAttrs" v-on="inputEvents" >
    </Throttling>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'
import Tag from './views/Tag.vue'
import Throttling from './views/Throttling.vue'

@Component({
  components: {
    Tag,
    Throttling
  }
})
export default class Example extends Vue {
  private tags!: string[]
  private data () {
    return {
      tags: ['tag1', 'tag2'],
      str: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">

</style>
