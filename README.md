# 数字计数器组件

> 数字计数器

## DEMO
![mbs-input-number.gif](https://upload-images.jianshu.io/upload_images/3175257-30f272543e9caceb.gif?imageMogr2/auto-orient/strip)


## Version

- 版本：v1.0.0

- 开发：mbs



## Usage

```javascript
templete:

<mbs-input-number
  v-model="num"
  :min="1" // 组件最小值
  :max="10" // 组件最大值
  :step="1" // 允许定义递增递减的步数控制
  size="medium" // 支持三种大小 medium small mini
  label="房间量" // 设置placehold文案
  > 
</mbs-input-number>

script:

import mbsInputNumber from 'mbs-input-number'

export default {
    name :'xxx',
    components: {
        mbsInputNumber
    },
    data() {
        return {
            num:1 // 初始化值（不可小于设置的min值,否则会被设置成min值）
        }
    }
}
```
## Installation

```
# install dependencies
npm install mbs-input-number --save

```

## option


Property | Description | type | default
---|---|---|---
disabled | 可设置组件不可用状态 | boolean | false
min | 组件最小值 | number | 
max | 组件最大值 | number | 
v-model | 初始值 | number | 
step | 递增递减的步数 | number | 1
size | 组件大小 | string | medium
label | placeholder值 | string | 



## 遗留问题
- [ ] 支持按钮位置调整（待实现）

## 更新记录

版本 | 更新项
---|---
v1.0.0 | 支持基本使用

## github
[mbs-input-number](https://github.com/weirui88888/mbs-input-number)
