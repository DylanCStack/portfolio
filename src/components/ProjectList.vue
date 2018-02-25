<template>
  <div>
    <ProjectItem v-for='(project, index) in projects' :project="project" :index='index' :visible='project.visible' :resize='resize' @inPosition='markLocation' :key="index">

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
      resize: false,
      resizeTimer: null,
      projects: [
        {
          title: 'Retro Desktop', // eslint-disable-next-line
          description: 'An Angular 2 recreation of an old windows desktop. Complete with a text-editor, paint program, and minesweeper.',
          images: [
            '/static/assets/RD-1.png',
            '/static/assets/RD-2.png',
            '/static/assets/RD-3.png',
            '/static/assets/RD-4.png',
            '/static/assets/RD-5.png',
            '/static/assets/RD-6.png',
          ],
          technologies: ['Angular 2', 'Express.js'],
          languages: ['Javascript', 'SQL'],
          top: 0,
          bottom: 0,
          visible: 0,
        },
        {
          title: 'Dnd Campaign Manager', // eslint-disable-next-line
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
        },
        {
          title: 'Global Disease Simulator', // eslint-disable-next-line
          description: 'An interactive simulation of a global pandemic made with vanilla javascript.',
          images: [
            '/static/assets/GDS-1.png',
            '/static/assets/GDS-2.png',
            '/static/assets/GDS-3.png',
            '/static/assets/GDS-4.png',
            '/static/assets/GDS-5.png',
          ],
          technologies: [],
          languages: ['Javascript'],
          top: 0,
          bottom: 0,
          visible: 0,
        },
      ],
    };
  },
  methods: {
    markLocation(data) {
      this.projects[data.index].top = data.top;
      this.projects[data.index].bottom = data.bottom;

      if (data.index === this.projects.length - 1) {
        this.resize = false;
      }
    },
    updateChildren() {
      // percent inset from top and bottom before element becomes (in)visible
      const inset = window.innerHeight * 0.10;
      const viewportTop = Math.ceil(window.pageYOffset + inset);
      const viewportBottom = Math.floor((viewportTop + window.innerHeight) - (inset * 2));
      for (let i = 0; i < this.projects.length; i++) {
        const project = this.projects[i];
        this.projects[i].visible = (project.bottom > viewportTop && project.top < viewportBottom);
      }
    },
    resizeChildren() {
      this.resize = true;
    },
  },
  beforeMount() {
    window.addEventListener('scroll', this.updateChildren);
    window.addEventListener('resize', () => {
      clearTimeout(this.resizeTimer);
      this.resizeTimer = setTimeout(() => {
        this.resizeChildren();
      }, 200);
    });
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.updateChildren);
    window.addEventListener('onresize', this.resizeChildren);
  },
};
</script>

<style lang="scss" scoped>

</style>
