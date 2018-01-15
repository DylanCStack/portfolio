<template>
  <div>
    <h3>{{project.title}}</h3>
    <p>{{project.description}}</p>
    <p><span v-for='technology in project.technologies'>{{technology}} </span><span v-for='language in project.languages'>{{language}} </span></p>
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
