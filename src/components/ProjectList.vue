<template>
  <div>
    <h1 id='header'>My projects.</h1>
    <ProjectItem v-for='(project, index) in projects' :project="project" :index='index' :opacity='project.opacity' @inPosition='markLocation' :key="index">

    </ProjectItem>
  </div>
</template>

<script>
import ProjectItem from '@/components/ProjectItem';

export default {
  name: 'ProjectList',
  components: { ProjectItem },
  data() {
    return {
      projects: [
        {
          title: 'Retro Desktop',
          description: 'An Angular 2 recreation of an old windows desktop. Complete with a text-editor, paint program, and minesweeper.',
          images: [
            '/static/assets/RD-1.png',
            '/static/assets/RD-2.png',
          ],
          technologies: ['Angular 2', 'Express.js'],
          languages: ['Javascript', 'SQL'],
          top: 0,
          bottom: 0,
          visible: 0,
          opacity: '',
        },
        {
          title: 'Dnd Campaign Manager',
          description: 'A D&D campaign manager made in Angular 2. It gives you the ability to create items, monsters, maps, and player characters. You can also limit the variety of monsters and items for ease of use when customizing your campaign.',
          images: [
            '/static/assets/CM-1.png',
            '/static/assets/CM-2.png',
            '/static/assets/CM-3.png',
            '/static/assets/CM-4.png',
            '/static/assets/CM-5.png',
            '/static/assets/CM-6.png',
            '/static/assets/CM-7.png',
          ],
          technologies: ['Angular 2', 'Firebase'],
          languages: ['Javascript'],
          top: 0,
          bottom: 0,
          visible: 0,
          opacity: '',
        },
        {
          title: 'Global Disease Simulator',
          description: 'An interactive simulation of a global pandemic made with vanilla javascript.',
          images: [
            '/static/assets/GDS-1.png',
            '/static/assets/GDS-2.png',
            '/static/assets/GDS-3.png',
            '/static/assets/GDS-4.png',
          ],
          technologies: [],
          languages: ['Javascript'],
          top: 0,
          bottom: 0,
          visible: 0,
          opacity: '',
        },
      ],
    };
  },
  methods: {
    markLocation(data) {
      this.projects[data.index].top = data.top;
      this.projects[data.index].bottom = data.bottom;
    },
    updateChildren() {
      const viewportTop = window.pageYOffset;
      const viewportBottom = viewportTop + window.innerHeight;
      for (let i = 0; i < this.projects.length; i++) {
        const project = this.projects[i];
        if (project.bottom > viewportTop && project.top < viewportBottom) {
          // let opacity = (opacity > 0 && opacity < 1) ? (viewportTop - project.top) / window.innerHeight : (opacity > 1) ? 1 : 0;
          const offset = (project.bottom - project.top);
          this.projects[i].opacity = ((viewportTop - project.top) + offset) / (window.innerHeight/2);
        }
      }
    },
  },
  beforeMount() {
    window.addEventListener('scroll', this.updateChildren);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.updateChildren);
  },
};
</script>

<style scoped>
#header {
  margin: 60px 10%;
  margin-bottom: 95vh;
  font-size: 5em;
}

</style>
