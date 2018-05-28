<template>
  <div class="wrapper" ref="wrapper">
    <ul class="content">
      <li v-for="(item,index) in 100" :key="index">{{item}}</li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    created () {}

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped >

</style>
