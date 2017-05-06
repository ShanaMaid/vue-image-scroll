<template lang="pug">
    ul.slider(
      :style="styleObject",
      @touchstart="handleDown",
      @mousedown="handleDown",
      @touchmove="handleMove",
      @mousemove="handleMove",
      @touchend="handleUp",
      @mouseup="handleUp")
        li(v-for="(item,index) in image", :class="[move[index]]")
          template(v-if="typeof item === 'object'")
            img(
              :src="item.src",
              :style="imgStyle",
              @click="target(index)")
            span(:class="{tag:item.tagName}", :style="item.tagStyle")
              | {{item.tagName}}
          template(v-if="typeof item === 'string'")
            img(
              :src="item",
              :style="imgStyle",
              @click="target(index)")
            em(
              v-for="(item,index) in image",
              @click="target(index)",
              :class="[move[index]]")
        li.button
          em(
            v-for="(item,index) in image",
            @click="target(index)",
            :class="[move[index]]")
        li.control
          em(@click="handlePre")
          em(@click="handleNext")
</template>
<script>
export default{
  name: 'slider',
  props: {
    styleObject: {
      default: {
        width: '750',
        height: '250'
      }
    },
    image: {
      require: true,
      type: Array,
      validator: function (value) {
        return value.length >= 3
      }
    },
    interval: {
      default: 2000
    },
    imgStyle: {
      default: {}
    },
    autoRoll: {
      default: true
    },
    direction: {
      default: 'left'
    }
  },
  mounted() {
    this.init();
  },
  data() {
    return {
      move: ['left', 'center', 'right'],
      isDown: false,
      dragStartX: 0,
      timer: null,
    }
  },
  methods: {
    init() {
      const width = parseInt(this.styleObject.width);
      const height = parseInt(this.styleObject.height);
      this.imgStyle.width = width * 0.7 + 'px';
      this.imgStyle.height = height * 0.9 + 'px';
      this.styleObject.width += 'px';
      this.styleObject.height += 'px';

      for (let i = 3; i < this.image.length; i++) {
        this.move[i] = 'wait';
      }

      if (this.autoRoll) this.setRoll();
    },
    setRoll() {
      if (this.direction === 'left') {
        this.timer = setInterval(this.nextPic, this.interval);
      }
      else {
        this.timer = setInterval(this.prePic, this.interval);
      }
    },
    nextPic(event) {
      let temp = this.move.pop();
      this.move.unshift(temp);
    },
    prePic(event) {
      let temp = this.move.shift();
      this.move.push(temp);
    },
    target(pos) {
      clearInterval(this.timer);
      const num = this.image.length;
      for (let i = 0; i < num; i++) {
        this.move[i] = 'wait';
      }
      this.move[pos] = 'center';
      this.move[pos + 1 < num ? pos + 1 : 0] = 'right';
      this.move[pos - 1 === -1 ? num - 1 : pos - 1] = 'left';
      this.move = this.move.concat();
      this.setRoll();
    },
    handleNext() {
      clearInterval(this.timer);
      this.nextPic();
      this.setRoll();
    },
    handlePre() {
      clearInterval(this.timer);
      this.prePic();
      this.setRoll();
    },
    handleDown(e) {
      if (!e.touches) e.preventDefault();
      this.isDown = true;
      this.dragStartX = ('ontouchstart' in window) ? e.touches[0].clientX : e.clientX;
    },
    handleMove(e) {
      e.preventDefault();
      if (!this.isDown) return;

      const eventPosX = ('ontouchstart' in window) ? e.touches[0].clientX : e.clientX;
      const deltaX = (this.dragStartX - eventPosX);

      clearInterval(this.timer);
      if (deltaX > 10) {
        this.handleUp();
        this.nextPic();
      }
      if (deltaX < -10) {
        this.handleUp();
        this.prePic();
      }
      this.setRoll();
    },
    handleUp() {
      this.isDown = false;
      this.dragOffset = 0;
    },
  }
}
</script>
<style scoped>
*{
  margin: 0;
  padding: 0;
}
.slider{
    perspective:1000px;
    position: relative;
}

.control em:first-child,
.control em:last-child{
    position:absolute;
    display: block;
    width: 30px;
    height: 30px;
    background-size: cover;
    z-index: 100;
    cursor: pointer;
}

.control em:first-child{
    left: 0px;
    background-image: url('../assets/pre.png');
}

.control em:last-child{
    right: 0px;
    background-image: url('../assets/next.png');
}

li{
    list-style-type: none;
    position: absolute;
    top: 0px;
    transition:transform 0.5s,scale 1s,left 1s,right 1s;
}

li.left,
li.right{
    transform: scale(0.9,0.9);
    z-index: 10;
}

li.left{
    left: -3%;
}

li.center{
    left: 15%;
    z-index: 100;
}

li.right{
    left: 33%;
}

li.wait{
    transform: scale(0,0);
}

.button{
    text-align: center;
    width: 100%;
    height: 20px;
    top: calc(100% - 20px);
}

.control{
    text-align: center;
    width: 100%;
    height: 30px;
    top: calc(50% - 20px);
    display: none;
    left: 0;
}

.slider:hover .control{
    display: inline-block;
}

.button em{
    display: inline-block;
    width: 20px;
    height: 5px;
    background-color: rgb(225,225,226);
    border-radius: 10px;
    margin: 0 2px;
    cursor: pointer;
}

em.center{
  background-color: rgb(198,47,47);
}

.tag{
  display: inline-block;
  padding: 5px;
  background-color: rgb(198,47,47);
  position: absolute;
  right: 0px;
  bottom: 15px;
  border-top-left-radius: 10px;
  font-size: 0.5rem;
  border-bottom-left-radius: 10px;
  color: white;
}

</style>
