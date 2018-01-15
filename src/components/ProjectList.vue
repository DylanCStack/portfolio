<template>
  <div>
    <h1>My projects.</h1>
    <ProjectItem v-for='project in projects' :project="project" :key="project.id">

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
          id: 0,
          title: 'Retro Desktop',
          description: 'An Angular 2 recreation of an old windows desktop. Complete with a text-editor, paint program, and minesweeper.',
          technologies: ['Angular 2', 'Express.js'],
          languages: ['Javascript', 'SQL'],
        },
        {
          id: 1,
          title: 'Dnd Campaign Manager',
          description: 'A D&D campaign manager made in Angular 2. It gives you the ability to create items, monsters, maps, and player characters. You can also limit the variety of monsters and items for ease of use when customizing your campaign.',
          technologies: ['Angular 2', 'Firebase'],
          languages: ['Javascript'],
        },
        {
          id: 2,
          title: 'Global Disease Simulator',
          description: 'An interactive simulation of a global pandemic made with vanilla javascript.',
          technologies: [],
          languages: ['Javascript'],
        },
      ],
    };
  },
};
</script>

<style scoped>

</style>
