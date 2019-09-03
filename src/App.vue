<template>
  <div id="app">
    <input v-model="nums">
    <Counter @count="count" v-for="n in getNum(nums)" v-bind:key="n" v-bind:msg="n"/>
    <span>Sum:{{sum}}</span>
  </div>
</template>

<script>
import Counter from './components/Counter.vue'
export default {
  name: 'App',
  components: {
    Counter
  },
  methods: {
    getNum: function (e) {
      let temp = 0
      let reg = /^[0-9]\d*$/
      if (!reg.test(e)) {
        return temp
      }
      temp = parseInt(e)
      return temp
    },
    count: function (e) {
      this.sum = this.sum + e
    }
  },
  data () {
    return {
      nums: 20,
      sum: 0
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
