<script lang="ts">
import { Component, Prop, Vue, Emit } from 'vue-property-decorator'
const lodash = require('lodash')

@Component({})
export default class Tag extends Vue {
  private newStr!: string
  @Prop() private value!: string
  private inputStr () {
    this.$emit('input', this.newStr)
  }
  private render () {
    return this.$scopedSlots.default({
      inputAttrs: {
        value: this.newStr
      },
      inputEvents: {
        input: (e: any)  => {
          this.newStr = e.target.value
          this.inputStr()
        }
      }
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">

</style>
