<template>
  <div id="app">
    <div class="header">
        vue-slider-163music<br>
        <a href="https://github.com/ShanaMaid/vue-slider-163music" class="btn">View on GitHub</a>
    </div>
    


    <div class="content">
      <div class="start">
        <h1>Quick Start</h1>
        <h2>Installation(安装)</h2>
        <div class="code white">
            <br>
            &nbsp&nbsp&nbsp npm install vue-163music-slider
            <br><br>
        </div>
        <br>
        <h2>Usage(使用方法)</h2>
        <div class="code white">
          <pre>
    &lt;template>
      &lt;div>
       &lt;slider v-bind="setting"></slider>
      &lt;/div>
    &lt;/template>

    &lt;script>
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
    &lt;/script>
          </pre>  
        </div>
        <br>
        <h2>Value-Default(默认值)</h2>
        <div class="code ">
          <pre>
  <span class="white">{</span>
    <span class="keyword">styleObject</span>:{
       width: '750',
       height: '250'
    }, <span class="gray">//滚动框样式 宽度默认750px 高度默认250px 其余样式小驼峰命名
        background-color => backgroundColor</span>
    <span class="keyword">imgSrc</span>: [
     'static/img/1-1.jpg', 
     'static/img/1-2.jpg', 
     'static/img/1-3.jpg', 
     'static/img/1-4.jpg', 
     'static/img/1-5.jpg'
    ],
    <span class="keyword">interval</span>:2000, <span class="gray">//滚动间隔,单位ms,默认2000</span>
    <span class="keyword">imgStyle</span>:null,<span class="gray">//图片样式，宽度和高度不可设置，样式名字小驼峰命名</span>
    <span class="keyword">autoRoll</span>:true, <span class="gray">//自动滚动</span>
    <span class="keyword">direction</span>:left <span class="gray">//滚动方向, left or right</span>
  <span class="white">}</span>
</pre>  
        </div>
      </div>

      <h1 class="example">Example</h1>
      <div class="item">
        <h1>default</h1>
        <slider class="innlineblock" v-bind="setting"></slider>
        <div class="code">
          <pre>
  <span class="white">{</span>
    <span class="keyword">imgSrc</span>: [
     'static/img/1-1.jpg', 
     'static/img/1-2.jpg', 
     'static/img/1-3.jpg', 
     'static/img/1-4.jpg', 
     'static/img/1-5.jpg'
    ]
  <span class="white">}</span>
          </pre>
      </div>
      </div>

      <div class="item">
        <h1>Setting1</h1>
        <slider class="innlineblock" v-bind="setting1"></slider>
        <div class="code">
          <pre>
  <span class="white">{</span>
    <span class="keyword">styleObject</span>: {
      width: '550',
      height: '250',
      backgroundColor: 'rgba(0,225,226,0.2)',
      borderRadius: '20px'
    },
    <span class="keyword">imgSrc</span>: [
    'static/img/1-1.jpg', 
    'static/img/1-2.jpg', 
    'static/img/1-3.jpg', 
    'static/img/1-4.jpg', 
    'static/img/1-5.jpg'],
    interval: 1000,
    <span class="keyword">imgStyle</span>: {
      borderRadius: '20px'
    },
   <span class="keyword">autoRoll</span>: true,
   <span class="keyword">direction</span>: 'right'
  <span class="white">}</span>
          </pre>
      </div>
      </div>

      <div class="item">
        <h1>Setting2</h1>
        <slider class="innlineblock" v-bind="setting2"></slider>
        <div class="code">
          <pre>
  <span class="white">{</span>
    <span class="keyword">styleObject</span>: {
      width: '250',
      height: '150'
    },
    <span class="keyword">imgSrc</span>: [
    'static/img/1-1.jpg', 
    'static/img/1-2.jpg', 
    'static/img/1-3.jpg', 
    'static/img/1-4.jpg', 
    'static/img/1-5.jpg'],
    <span class="keyword">imgStyle</span>: {
      borderRadius: '20px'
    },
    <span class="keyword">autoRoll</span>: false,
   <span class="white">}</span>
          </pre>
      </div>
      </div>

    </div>
  </div>
</template>

<script>
import slider from './components/Slider'

export default {
  name: 'app',
  components: {
    slider
  },
  data () {
    return {
      setting: {
        imgSrc: ['static/img/1-1.jpg', 'static/img/1-2.jpg', 'static/img/1-3.jpg', 'static/img/1-4.jpg', 'static/img/1-5.jpg']
      },
      setting1: {
        styleObject: {
          width: '550',
          height: '250',
          backgroundColor: 'rgba(0,225,226,0.2)',
          borderRadius: '20px'
        },
        imgSrc: ['static/img/1-1.jpg', 'static/img/1-2.jpg', 'static/img/1-3.jpg', 'static/img/1-4.jpg', 'static/img/1-5.jpg'],
        interval: 1000,
        imgStyle: {
          borderRadius: '20px'
        },
        autoRoll: true,
        direction: 'right'
      },
      setting2: {
        styleObject: {
          width: '250',
          height: '150',
        },
        imgSrc: ['static/img/1-1.jpg', 'static/img/1-2.jpg', 'static/img/1-3.jpg', 'static/img/1-4.jpg', 'static/img/1-5.jpg'],
        imgStyle: {
          borderRadius: '20px'
        },
        autoRoll: false,
        direction: 'right'
      }
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
}

.header{
  height: 340px;
  background-color: #159957;
  background-image: linear-gradient(120deg, #155799, #159957);
  padding: 140px 0;
  color: white;
  font-weight: bolder;
  font-size: 3rem;
}

.content{
  margin: 0 auto;
  width: 750px;

}

.btn {
  text-decoration: none;
  box-sizing: content-box;
  font-size: 1.1rem;
  display: inline-block;
  margin-bottom: 1rem;
  color: rgba(255, 255, 255, 0.7);
  background-color: rgba(255, 255, 255, 0.08);
  border-color: rgba(255, 255, 255, 0.2);
  border-style: solid;
  border-width: 1px;
  border-radius: 0.3rem;
  transition: color 0.2s, background-color 0.2s, border-color 0.2s;
  padding: 0.75rem 1rem;
}

.btn:hover {
    color: rgba(255, 255, 255, 0.8);
    text-decoration: none;
    background-color: rgba(255, 255, 255, 0.2);
    border-color: rgba(255, 255, 255, 0.3);
}

.innlineblock{
  display: inline-block;
}

.code{
  text-align: left;
  background-color: rgb(51,51,51);
  color: #ffd400;
  font-weight: bold;
  font-size: 1.2rem;
}

.keyword{
  color: #2ecc71;
}

.white{
  color: white;
}

pre{
  padding: 0px;
}

.item{
  background-color: white;
  box-shadow: 0px 5px 100px black;
  padding: 10px 0px;
  margin: 20px 0;
}

.item h1{
  padding: 10px 30px;
  text-align: left;
  color: #f05b72;
}

.start h1{
  margin: 20px 0px;
}

.start h2{
  text-align: left;
  margin: 10px 0;
}

.gray{
  color: rgb(224,224,224);
}

.example{
  margin: 50px 0;
}
</style>
