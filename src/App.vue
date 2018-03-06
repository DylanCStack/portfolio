<template>
  <div id="app">
    <header id='header'>
      <h1 id='title'>{{title}}</h1>
      <p id='summary'>{{summary}}</p>
    </header>
    <router-view/>
    <footer id='contact'>
      <p><a v-for='contact of contactInfo' :href='contact.link'>{{contact.text}}</a></p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      title: 'My projects.', // eslint-disable-next-line
      summary: 'Hello you! My name is Dylan Stackhouse. I am a junior developer in Portland, OR with experience working with AR, 3D, QA, and web development. My latest passions are personal automation and visualization.',
      contactInfo: [
        {
          text: 'Stackhouse.Dylan@gmail.com',
          link: 'mailto:Stackhouse.Dylan@gmail.com',
        },
        {
          text: 'Linkedin/dylan-stackhouse',
          link: 'https://www.linkedin.com/in/dylan-stackhouse/',
        },
        {
          text: 'GitHub/DylanCStack',
          link: 'https://github.com/DylanCStack',
        },
      ],
    };
  },
};
</script>

<style lang="scss">
$guide-color: #bbbbbb;

$circle-position: 10%;
$circle-box-size: 85vh 85vh;
$circle-gradient: $guide-color 90%, $primary-color 91%, $primary-color 94%, transparent 95%;
$mask-size: 100% 82vh;
$dash-size: 4vh 15vh;

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 0 0 1px;
  margin: 0;
  color: white;

  background:
    radial-gradient(circle closest-side at 50% 100-$circle-position, $circle-gradient),
    radial-gradient(circle closest-side at 50% 0+$circle-position, $circle-gradient),
    linear-gradient($primary-color, $primary-color),
    linear-gradient($primary-color, $primary-color),
    linear-gradient($primary-color 10%, $guide-color 11%, $guide-color 79%, $primary-color 80%);
  background-repeat: no-repeat, no-repeat, no-repeat, no-repeat, repeat-y;
  background-position: 50% top, 50% bottom, top, bottom, 50% 20vh;
  background-size: $circle-box-size, $circle-box-size, $mask-size, $mask-size, $dash-size;
}
* {
  border:0;
  margin:0;
}
body{
  background-color:$primary-color;
}
#header {
  margin: 60px 10%;
  margin-bottom: 95vh;

  #title {
    font-size: 13vw;
  }
  #summary {
    margin: 30px 0;
  }
  @include media($media-s){
    #title {
      font-size: 5em;
      width: 65vw;
      margin: 15vw auto;
    }
    #summary {
      font-size: 20px;

      margin: 10vw auto;
      width: 65vw;
      max-width: 850px;
    }
    @include media($media-m) {
      #title {
        margin: 0 auto;
        max-width: 850px;
      }
      #summary {
        font-size: 25px;
      }
    }
  }
}
footer#contact{
  width: 100%;
  p {
    width:100%;
    text-align: center;
    margin-bottom: 2%;
    a {
      &:not(:first-of-type)::before {
        content: ' | ';
      }
      color: $primary-color-lighter;
      &:visited {
        color: $primary-color-lighter;
      }
    }
  }
}
</style>
