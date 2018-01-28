<template>
  <div class='project-item'>
    <div class='bg' :style='bgStyle'>
      <carousel :images='project.images'></carousel>
      <div class='text'>
        <h3 class='title'>{{project.title}} {{opacity}}</h3>
        <p class='description'>{{project.description}}</p>
        <p class='tech-list'><span class='tech' v-for='technology in project.technologies'>{{technology}}</span><span class='language' v-for='language in project.languages'>{{language}} </span></p>
      </div>
    </div>
  </div>
</template>

<script>
import Carousel from '@/components/Carousel';

export default {
  name: 'ProjectItem',
  components: { Carousel },
  props: ['project', 'index', 'opacity'],
  data() {
    return {
      bgStyle: {
        'background-image': `url( ${this.project.images[0]})`,
        opacity: this.opacity,
      },
    };
  },
  methods: {},
  watch: {
    opacity() {
      this.bgStyle.opacity = this.opacity;
    },
  },
  mounted() {
    const top = this.$el.offsetTop;
    this.$emit('inPosition', {
      index: this.index,
      top,
      bottom: top + this.$el.offsetHeight,
    });
  },
};
</script>

<style scoped>
.project-item {
  margin: 65vh 0;
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

}

</style>
