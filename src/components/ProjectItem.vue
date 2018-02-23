<template>
  <div class='project-item'>
    <div :class='["bg", visible ? "animateIn" : "animateOut"]' :style='bgStyle'>
      <div class='details'>
        <carousel :images='project.images'></carousel>
        <div class='text'>
          <h3 class='title'>{{project.title}}</h3>
          <p class='description'>{{project.description}}</p>
          <p class='tech-list'><span class='tech' v-for='technology in project.technologies'>{{technology}}</span><span class='language' v-for='language in project.languages'>{{language}} </span></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Carousel from '@/components/Carousel';

export default {
  name: 'ProjectItem',
  components: { Carousel },
  props: ['project', 'index', 'resize', 'visible'],
  data() {
    return {
      bgStyle: {
        'background-image': `url( ${this.project.images[0]})`,
      },
    };
  },
  methods: {
    emitPosition() {
      const top = this.$el.offsetTop;
      this.$emit('inPosition', {
        index: this.index,
        top,
        bottom: top + this.$el.offsetHeight,
      });
    },
  },
  watch: {
    resize() {
      // on resize this will trigger and re-mark the project locations.
      this.emitPosition();
    },
  },
  mounted() {
    this.emitPosition();
  },
};
</script>

<style lang="scss" scoped>
$language-color: #ff5500;

.project-item {
  margin: 0 0 85vh ;
}

.project-item>*{
  padding:20px 0 0 3%;
}

.project-item .bg {
  height: 95vh;
  width: 100%;
  border-top: 2px solid;
  border-bottom: 2px solid;
  margin:0;
  padding: 0;
}
.bg {
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  animation-timing-function: ease-in;
  animation-duration: 500ms;
}

.animateIn{
   animation-name: animateIn;
   opacity: 1;
}

.animateOut{
   animation-name: animateOut;
   opacity: 0;
}

@keyframes animateIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@keyframes animateOut {
  from {
    opacity: 1;
  }

  to {
    opacity: 0;
  }
}

.details {
  background:rgba($primary-color-darker, .825);

  min-height: 35%;
  padding: 20px;
  margin: 10px;

  border-radius: 6px;
  border-style: ridge;
  border: 2px outset rgba(255, 255, 255, 0.2);
}

.carousel {
  margin: 0 2%;
}
.text {
  padding: 2%;
}
.title {
  margin: 1%;
}

.description {

}

.tech-list>* {
  margin-right:0.3em;
}

.tech {

}

.language {
 color:$language-color;
}

</style>
