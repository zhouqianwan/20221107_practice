<template>
  <div>
    <h1 v-color="'red'">这是vue 组件</h1>
    <h1 v-yellow="'yellow'" v-bgc="'orange'">这是黄色的字体</h1>
    <h1 v-color="colors" v-size="'50px'">这是紫色的文字</h1>
    <h1 v-color="colo">这是#eeeddd</h1>
    <button @click="colors = 'red'" v-bgc="'purple'">颜色变成红色</button>
    <button @click="colors = 'pink'">颜色变成粉色</button>
    <button @click="colo = 'black'">变成黑色</button>
    <button @click="getInfo">获取数据</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      colors: 'purple',
      colo: '#eeeddd'
      // nihao
    }
  },
  methods: {
    async  getInfo () {
      const { data: res } = await axios.get('http://www.liulongbin.top:3006/api/get')
      console.log(res)
    }
  },
  directives: {
    color (el, binding) {
      el.style.color = binding.value
    },
    yellow: {
      bind (el, binding) {
        el.style.color = binding.value
      }
    },
    size (el, binding) {
      el.style.fontSize = binding.value
    }
  }
}
</script>

<style lang="less" scoped></style>
