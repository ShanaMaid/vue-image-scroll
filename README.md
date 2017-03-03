# vue-slider-163music
[![build](https://img.shields.io/wercker/ci/wercker/docs.svg)](https://github.com/ShanaMaid/vue-slider-163music) 
[![build](https://img.shields.io/badge/npm-1.0.6-blue.svg)](https://github.com/ShanaMaid/vue-slider-163music) 
[![build](https://img.shields.io/npm/l/express.svg)](https://github.com/ShanaMaid/vue-slider-163music)

一个模仿网易云音乐的vue图片滚动插件

[Live Demos](http://blog.shanamaid.top/vue-slider-163music/example)

[Documention](http://blog.shanamaid.top/vue-slider-163music/example)

based on vue 2.0

## Install
```
npm install vue-163music-slider 
```

### Local
```
git clone  https://github.com/ShanaMaid/vue-slider-163music.git

#安装依赖
npm install 

#启动
npm run dev

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
- image add tagName and tagStyle

## Opitions
### Props
| Props     | Type    | Default | Description |
|-----------|---------|---------|-------------|
|styleObject| Object  | {width:'750',height:'240'}|scroll box style,please use lower camel case, eg: background-color => backgroundColor|
|image      | Array   | null    | imgae source path ,tagName,tagStyle; length >= 3|
|interval   | Integer | 2000    | unit: ms, rolling interval |
|imgStyle   | Object  | null    | image style, the same as `styleObject`  |
|autoRoll   | Boolean | true    |  `true` or `false` |
|direction  | String  | left    | scroll direction, `left` or `right` |


## To do
- [x] Basics
- [x] add tag for image

more!!

## License

[MIT](https://github.com/ShanaMaid/vue-slider-163music/blob/master/LICENSE)