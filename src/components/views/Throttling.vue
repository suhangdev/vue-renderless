<script lang="ts">
import { Component, Prop, Vue, Emit } from 'vue-property-decorator'

@Component({})
export default class Tag extends Vue {
  private newStr!: string
  private curTime!: number
  private clock: any
  @Prop() private value!: string
  @Prop() private delay!: number
  private inputStr () {
    this.$emit('input', this.newStr)
  }
  private throttle (now: number, delay: number) {
    let that = this
    if (!this.curTime) {
      this.curTime = 0
    }
    if (+new Date() - this.curTime - delay > 0) {
      this.clock = setTimeout(() => {
        that.inputStr()
      }, delay)
    } else {
      if (this.clock) {
        clearTimeout(this.clock)
        this.clock = null
      }
      this.clock = setTimeout(() => {
        that.inputStr()
      }, delay)
    }
    this.curTime = now
  }
  private render () {
    return this.$scopedSlots.default({
      inputAttrs: {
        value: this.newStr
      },
      inputEvents: {
        input: (e: any)  => {
          this.newStr = e.target.value
          let time: number
          time = +new Date()
          this.throttle(time, this.delay)
        }
      }
    })
  }
}
</script>
