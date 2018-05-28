<template>
  <div id="app">
    <div class="tab" ref="tab">
      <ul  class="wrapper" ref="wrapper">
        <li v-for="(item,index) in 100" class="tabitem" ref="tabitem" :key="index">{{item}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
export default {
  props: {
    /** * 是否开启横向滚动 */ scrollX: { type: Boolean, default: true }
  },
  name: 'App',
  created () {
    this.$nextTick((res) => {
      this.initScroll()
    })
  },
  methods: {
    initScroll () {
      let width = 0
      for (var i = 0; i < 100; i++) {
        width += this.$refs.tabitem[0].getBoundingClientRect().width
      }
      // console.log(width)
      this.$refs.wrapper.style.width = width + 'px'

      if (!this.scroll) {
        this.$nextTick(() => {
          this.scroll = new Bscroll(this.$refs.tab, {
            startX: 0,
            click: true,
            scrollX: true
          })
        })
      } else {
        this.scroll.refresh()
      }
    }
  }
}
</script>

<style>
body,
html {
  height: 100%;
}
ul li {
  list-style: none;
}
.tab{
  overflow: hidden;
  width:100vw;
}
.wrapper {
  padding:0;
  display: flex;
}
.tabitem {
  flex:0 0 60px;
  width:40px;
  background: yellow;
}
</style>
