<script lang="ts">
import { Component, Prop, Vue, Emit } from 'vue-property-decorator'

@Component({})
export default class Tag extends Vue {
  private newTag!: string
  @Prop() private value!: string[]
  @Emit() private removeTag (tag: string) {
    this.value.forEach((item, index) => {
      if (item === tag) {
        this.value.splice(index, 1)
      }
    })
  }
  private addTag () {
    if (this.newTag.trim().length === 0 || this.value.includes(this.newTag.trim())) {
      return
    }
    let tempStr: string
    tempStr = this.newTag.trim()
    this.newTag = ''
    this.value.push(tempStr)
  }
  private render () {
    return this.$scopedSlots.default({
      tags: this.value,
      removeTag: this.removeTag,
      inputAttrs: {
        value: this.newTag
      },
      inputEvents: {
        input: (e: any) => {
          this.newTag = e.target.value
        },
        keydown: (e: any) => {
          if (e.keyCode === 13) {
            e.preventDefault()
            this.addTag()
          }
        }
      },
      addTag: this.addTag
    })
  }
}
</script>
