<template>
  <div>
    <h3>{{project.title}}</h3>
    <p>{{project.description}}</p>
  </div>
</template>

<script>
export default {
  name: 'ProjectItem',
  components: { /* carousel here */},
  props: ['project'],
  data() {
    return {

    };
  },
};
</script>

<style scoped>

</style>
