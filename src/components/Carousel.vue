<template>
  <div class='carousel' >
    <div v-for='n in (inLightbox ? 2 : 1)'>
      <div class='slides-container'>
        <img v-for='(image, index) in images':key='index' :class='["slide", getOrder(index)]' :src='images[index]'/>
      </div>
      <div class='controls' v-on:click='lightbox($event)'>
        <button class='btn-left' v-on:click='previous'><img src='/static/assets/svg/arrow.svg'/></button>
        <button class='btn-right' v-on:click='next'><img src='/static/assets/svg/arrow.svg'/></button>
      </div>
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
      inLightbox: false,
      autoID: 0,
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
    lightbox(e) {
      if (e.target.tagName !== 'BUTTON' && e.target.tagName !== 'IMG') {
        this.inLightbox = !this.inLightbox;
      }
    },
    previous() {
      this.motion = 'left';
      this.focus = ((this.focus + (this.images.length - 1)) % this.images.length);
      this.autoplay();
    },
    next() {
      this.motion = 'right';
      this.focus = (this.focus + 1) % this.images.length;
      this.autoplay();
    },
    autoplay() {
      clearInterval(this.autoID);
      this.autoID = setInterval(() => {
        this.next();
      }, 7000);
    },
  },
  mounted() {
    this.autoplay();
  },
};
</script>

<style lang="scss" scoped>
.carousel {
  position: relative;
  min-width: 50%;

  @include media($media-m) {
    min-width: 0;
    max-width: 50%;
    display: inline-block;
  }

  .slides-container {
    position:relative;
    overflow: hidden;

    .slide {
      position: absolute;
      left: 0px;
      top: 50%;
      transform: translateY(-50%);

      max-width: 100%;
      height: auto;

      transition: left 0.25s;

      &.slide-right {
        left: 100%;
      }
      &.slide-focus {
        left: 0%;
        position: static;
        transform: none;
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


    button {
      $button-transition-timing: 0.75s ease-out;

      position: relative;
      top: 0;

      outline:none;

      background: transparent;
      height: 100%;
      width: 15%;

      opacity: 0.2;
      transition: opacity $button-transition-timing;

      &:hover {
        opacity:1;
        img {
          background: none;
          &:hover {
            opacity: 1;
          }
        }
      }
      img {
        position: absolute;
        top: 50%;
        width: 50%;
        height: auto;
        padding: 15%;

        $border-radius: 50%;
        border-radius: 0 $border-radius $border-radius 0;
      }
      &.btn-left {
        float: left;
        background: linear-gradient(-90deg, transparent, rgba(0, 0, 0, 0.6));

        img {
          left: 0;
          transform: translate(-30%, -50%) rotate(180deg);
        }
      }
      &.btn-right {
        float: right;
        background: linear-gradient(90deg, transparent, rgba(0, 0, 0, 0.6));

        img {
          right: 0;
          transform: translate(30%, -50%);
        }
      }
    }
  }
  &>div:nth-of-type(2) {
    &:before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: rgba(0, 0, 0, 0.7);
    }
    position: fixed;
    top: 15%;
    left:0;
    width: 100vw;
    height: auto;
  }
}
</style>
