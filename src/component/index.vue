<template>
    <div class="mbs-input-number-container clearfix" :class="{disabled:disabled}">
        <button class="fl mbs-btn mbs-btn-left" type="button" @click="reduce" :class="[{reduceDisable:reduceDisable,mbsBtnDisable:disabled},size]">-</button>
        <input  class="fl mbs-input" type="text" :value="val" :disabled="disabled" :class="[{mbsInputDisable:disabled},size]" @change="handleInputChange($event)" :placeholder="label">
        <button class="fl mbs-btn mbs-btn-right" type="button" @click="add" :class="[{addDisable:addDisable,mbsBtnDisable:disabled},size]">+</button>
    </div>
</template>

<script>
export default {
  name: 'mbs-input-number',
  props: {
    label: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: false
    },
    value: {
      type: [Number, String]
    },
    min: {
      type: Number
    },
    max: {
      type: Number
    },
    step: {
      type: Number,
      default: 1
    },
    size: {
      type: String,
      default: 'medium'
    }
  },
  computed: {
    addDisable () {
      if (this.max <= this.val) {
        return true
      }
      return false
    },
    reduceDisable () {
      if (this.val <= this.min) {
        return true
      }
      return false
    },
    val: {
      get () {
        //   判断传入value是否小于设置的min值
        if (this.value < this.min) {
          this.$emit('input', this.min)
          return this.min
        }
        return this.value
      },
      set (v) {
        this.$emit('input', v)
      }
    }
  },
  methods: {
    add () {
      if (this.disabled) return
      if (this.val + this.step > this.max) {
        return false
      }
      this.val += this.step
    },
    reduce () {
      if (this.disabled) return
      if (this.val - this.step < this.min) {
        return false
      }
      this.val -= this.step
    },
    handleInputChange (e) {
      let targetValue = e.target.value
      if (isNaN(targetValue)) {
        e.target.value = this.max
        this.$emit('input', this.max)
        return
      }
      if (targetValue === '') {
        e.target.value = this.min
        this.$emit('input', this.min)
        return
      }
      if (Number(targetValue) > this.max) {
        e.target.value = this.max
        this.$emit('input', this.max)
        return
      }
      if (Number(targetValue) < this.min) {
        e.target.value = this.min
        this.$emit('input', this.min)
        return
      }
      this.$emit('input', targetValue)
    }
  }
}
</script>

<style>
.clearfix::after{
    content: '';
    display: block;
    clear: both;
}
.fl{
    float: left;
}
.mbs-btn{
    padding: 6px 12px;
    font-size: 14px;
    outline: none;
    background: #f5f7fa;
}
.mbs-btn:hover{
    color:#409eff;
}
.mbs-btn.medium{
    padding: 6px 12px;
    font-size: 17px;
    outline: none;
    background: #f5f7fa;
}
.mbs-btn.small{
    padding: 3px 8px;
    font-size: 13px;
    outline: none;
    background: #f5f7fa;
}
.mbs-btn.mini{
    padding: 2px 7px;
    font-size: 12px;
    outline: none;
    background: #f5f7fa;
}
.mbs-input{
    text-align: center;
    padding: 5px 0;
    width: 100px;
    outline: none;
}
.mbs-input.medium{
    text-align: center;
    padding: 7px 0;
    width: 150px;
    outline: none;
}
.mbs-input.small{
    text-align: center;
    padding: 3px 0;
    width: 100px;
    outline: none;
}
.mbs-input.mini{
    text-align: center;
    padding: 0 0;
    width: 60px;
    outline: none;
}
.mbs-btn.mbsBtnDisable,.mbs-input.mbsInputDisable{
    cursor: not-allowed;
    color:#e4e7ed;
}
.mbs-btn-left{
    border-top-left-radius: 4px;
    border-bottom-left-radius: 4px;
    border-right: none;
}
.mbs-btn-left.reduceDisable{
    cursor: not-allowed;
    color: #ccc;
}
.mbs-btn-right{
    border-top-right-radius: 4px;
    border-bottom-right-radius: 4px;
    border-left: none;
}
.mbs-btn-right.addDisable{
    cursor: not-allowed;
    color: #ccc;
}

</style>
