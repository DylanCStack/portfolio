<template>
  <div class='carousel'>
    <div class='slides-container'>
      <img v-for='(image, index) in images':key='index' :class='["slide", getOrder(index)]':src='images[index]'/>
    </div>
    <div class='controls'>
      <button class='btn-left' v-on:click='previous'><img src='/static/assets/svg/arrow.svg'/></button>
      <button class='btn-right' v-on:click='next'><img src='/static/assets/svg/arrow.svg'/></button>
    </div>
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

<style lang="scss" scoped>
.carousel {
  float: left;
  position: relative;
  min-width: 50%;

  .slides-container {
    min-height: 30vw;
    min-width: 40vw;
    position:relative;
    overflow: hidden;

    .slide {
      position: absolute;
      left: 0px;
      top: 50%;
      transform: translateY(-50%);

      width: 100%;
      height: auto;

      transition: left 0.25s;

      &.slide-right {
        left: 100%;
      }
      &.slide-focus {
        left:0%;
      }
      &.slide-left {
        left: -100%;
      }
      &.slide.slide-behind {
        z-index: -1;
      }
    }
  }
  .controls {
    position: absolute;
    top:0;
    left:0;

    height: 100%;
    width: 100%;
    opacity: 1;

    transition: opacity 0.25s;

    button {
      position: relative;
      top: 0;

      outline:none;

      background: transparent;
      height: 100%;
      width: 15%;

      img {
        position: absolute;
        top: 50%;
        width: 50%;
        height: auto;
        padding: 15%;

        $border-radius: 50%;
        border-radius: 0 $border-radius $border-radius 0;

        opacity: 0.6;
        background: radial-gradient(circle closest-side at 50% 50%, rgba(0, 0, 0, 0.6) 40%, transparent);
      }
      &.btn-left {
        float: left;

        &:hover {
          background: linear-gradient(-90deg, transparent, black);
        }

        img {
          left: 0;
          transform: translate(-30%, -50%) rotate(180deg);
        }
      }
      &.btn-right {
        float: right;

        &:hover {
          background: linear-gradient(90deg, transparent, black);
        }

        img {
          right: 0;
          transform: translate(30%, -50%);
        }
      }
    }
  }
}
</style>
