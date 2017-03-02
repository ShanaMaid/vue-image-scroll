# vue-slider-163music
[![build](https://img.shields.io/wercker/ci/wercker/docs.svg)](https://github.com/ShanaMaid/vue-slider-163music) 
[![build](https://img.shields.io/badge/npm-1.0.4-blue.svg)](https://github.com/ShanaMaid/vue-slider-163music) 
[![build](https://img.shields.io/npm/l/express.svg)](https://github.com/ShanaMaid/vue-slider-163music)

一个模仿网易云音乐的vue图片滚动该插件

[Live Demos](http://blog.shanamaid.top/vue-slider-163music/examlple)

[Documention](http://blog.shanamaid.top/vue-slider-163music/examlple)

based on vue 2.0

## Install
```
npm install vue-163music-slider 
```


## Usage
```
<template>
  <div>
    <slider v-bind="setting">
  </div>
</template>

<script>
import slider from 'vue-slider-163music';

export default {
  components: {
    slider
  },
  data: function() {
    return {
      setting: {
        imgSrc: ['1.jpg', '2.jpg', '3.jpg']
      }
    }
  }
}
</script>          
```




## Update
- finish basics


## Opitions
### Props
| Props     | Type    | Default | Description |
|-----------|---------|---------|-------------|
|styleObject| Object  | {width:'750',height:'240'}|scroll box style,please use lower camel case, eg: background-color => backgroundColor|
|imgSrc     | Array   | null    | imgae source path, length >= 3|
|interval   | Integer | 2000    | unit: ms, rolling interval |
|imgStyle   | Object  | null    | image style, the same as `styleObject`  |
|autoRoll   | Boolean | true    |  `true` or `false` |
|direction  | String  | left    | scroll direction, `left` or `right` |


## To do
- [x] Basics
- [ ] add tag for image

more!!

## License

[MIT](https://github.com/ShanaMaid/vue-slider-163music/blob/master/LICENSE)