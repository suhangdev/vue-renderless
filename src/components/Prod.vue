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
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'
import Tag from './views/Tag.vue'

@Component({
  components: {
    Tag
  }
})
export default class Prod extends Vue {
  private tags!: string[]
  private data () {
    return {
      tags: ['tag1', 'tag2']
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">

</style>
