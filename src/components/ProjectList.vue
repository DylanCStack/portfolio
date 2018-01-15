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
          title: 'Project One',
          description: 'The first of three projects.',
        },
        {
          id: 1,
          title: 'Project Two',
          description: 'The second of three projects.',
        },
        {
          id: 2,
          title: 'Project Three',
          description: 'The last of three projects.',
        },
      ],
    };
  },
};
</script>

<style scoped>

</style>
