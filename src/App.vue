<template>
  <div id="app">
      <div class="demo">
          <mbs-input-number
          v-model="num"
          :min="1"
          :max="11"
          :step="1"
          label="房间量">
          </mbs-input-number>
          <h3>您选择的数量为{{num}}</h3>
      </div>
  </div>
</template>

<script>
import mbsInputNumber from './component/index'
export default {
  name: 'app',
  components: {
    mbsInputNumber
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      num: 4
    }
  },
  methods: {
    getval (val) {
      console.log(val)
    }
  }
}
</script>

<style>
  .demo{
    width: 400px;
    margin: 0 auto;
    padding-top: 50px;
  }
</style>
