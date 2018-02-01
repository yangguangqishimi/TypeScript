<template>
  <div>
    <wxc-button :btnStyle="{height: 150}" text="平移" @wxcButtonClicked="onTranlate"></wxc-button>
    <wxc-button :btnStyle="{height: 150}" text="复位" style="margin-top:20" @wxcButtonClicked="reset"></wxc-button>
    <div ref="box" class="box" :style="{transform: `translateX(${x})`}" ></div>
  </div>  
</template>

<script>
import { WxcButton } from 'weex-ui'
export default {
  components: { WxcButton },
  data () {
    return {
      x: 0
    }
  },
  methods: {
    onTranlate () {
      this.x = 100
      this.onAnimation()
    },
    onAnimation () {
      weex.requireModule('animation').transition(this.$refs.box, {
        styles: {
          transform: 'translateX(250)'
        },
        duration: 1000,
        timingFunction: 'linear',
        delay: 0
      }, () => {
        this.x = 250
      })
    },
    reset () {
      this.x = 0
    }
  }
}
</script>

<style scoped>
.box {
  width: 500;
  height: 200;
  background-color: #309bf8;
  margin-top: 50;
}
</style>
