<template>
  <div class='project-item'>
    <img src=''/>
    <h3 class='title'>{{project.title}}</h3>
    <p class='description'>{{project.description}}</p>
    <p class='tech-list'><span class='tech' v-for='technology in project.technologies'>{{technology}}</span><span class='language' v-for='language in project.languages'>{{language}} </span></p>
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
.project-item {
  margin: 30px 0;
}

.project-item>*{
  padding:20px 0 0 3%;
}

.project-item img {
  height: 75vh;
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
