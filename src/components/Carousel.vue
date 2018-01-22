<template>
  <div class='carousel'>
    <div class='slides-container'>
      <img v-for='(image, index) in images':key='index' :class='["slide", getOrder(index)]'/>
    </div>
    <button class='controls btn-left' v-on:click='previous'></button>
    <button class='controls btn-right' v-on:click='next'/></button>
  </div>
</template>

<script>
export default {
  name: 'Carousel',
  props: ['images'],
  data() {
    return {
      motion: '',
      focus: 0,
    };
  },
  methods: {
    getOrder(index) {
      if (index === this.focus) {
        return 'slide-focus';
      } else if (index === (this.focus + this.images.length + 1) % this.images.length) {
        // eslint-disable-next-line
        return 'slide-right' + (this.motion === 'right' ? ' slide-behind' : '');
      }
      // eslint-disable-next-line
      return 'slide-left' + (this.motion === 'left' ? ' slide-behind' : '');
    },
    previous() {
      this.motion = 'left';
      this.focus = ((this.focus + (this.images.length - 1)) % this.images.length);
    },
    next() {
      this.motion = 'right';
      this.focus = (this.focus + 1) % this.images.length;
    },
  },
};
</script>

<style scoped>
.carousel {
  float: left;
  position: relative;
}
img, .slides-container {
  height: 90px;
  width: 160px;
}
img:nth-of-type(1){
  background-color: red;
}
img:nth-of-type(2){
  background-color: green;
}
img:nth-of-type(3){
  background-color: blue;
}
.slides-container {
  position:relative;
  overflow: hidden;
}
.slide {
  position: absolute;
  top: 0px;
  left: 0px;

  transition: left 0.25s;
}
.slide-right {
  left: 100%;
}
.slide-focus {
  left:0;
}
.slide-left {
  left: -100%;
}
.slide.slide-behind {
  z-index: -1;
}
.controls {
  position: absolute;
  top: 10%;
  height: 80%;
  width: 5%;
  opacity: 0.6;

  transition: opacity 0.25s;
}
.controls:hover {
  opacity: 1;
}
.btn-left {
  left: -2.5%;
}
.btn-right {
  right: -2.5%;
}
</style>
