<template>
  <div class='project-item'>
    <div class='bg'>
      <carousel :images='images'></carousel>
      <h3 class='title'>{{project.title}}</h3>
      <p class='description'>{{project.description}}</p>
      <p class='tech-list'><span class='tech' v-for='technology in project.technologies'>{{technology}}</span><span class='language' v-for='language in project.languages'>{{language}} </span></p>
    </div>
  </div>
</template>

<script>
import Carousel from '@/components/Carousel';

export default {
  name: 'ProjectItem',
  components: { Carousel },
  props: ['project'],
  data() {
    return {
      images: [
        {
          url: 'fake path',
        },
        {
          url: 'fake path',
        },
        {
          url: 'fake path',
        },
      ],
    };
  },
};
</script>

<style scoped>
.project-item {
  margin: 30px 0;
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

.title {

}

.desctiption {

}

.tech-list>* {
  margin-right:0.3em;
}

.tech {

}

.language {

}

</style>
