<template>
  <div id="app">
    <Nav />
    <div class="sections v-scroll-spy">
      <Landing/>
      <About @clicked="scroll('About')" />
      <Experience @clicked="scroll('Experience')"/>
      <Skills @clicked="scroll('Skills')"/>
      <Projects @clicked="scroll('Projects')"/>
      <Contact @clicked="scroll('Contact')"/>
    </div>
  </div>
</template>

<script>
import Nav from './Sections/Nav.vue'
import Landing from './Sections/Landing.vue'
import About from './Sections/About.vue'
import Experience from './Sections/Experience.vue'
import Projects from './Sections/Projects.vue'
import Contact from './Sections/Contact.vue'
import Skills from './Sections/Skills.vue'
export default {
  name: 'App',
  components: {
    Nav,
    Landing,
    About,
    Experience,
    Projects,
    Contact,
    Skills,
  },
  methods: {
      scroll(id) {  
      document.getElementById(id).scrollIntoView({
        behavior: "smooth"
      });
    }
  }

}
</script>

<style>
:root{
  --black: #161616;
  --black2: #292929;
  --grey: #b8b8b8;
  --darkgreen: 	#346751;
  --peach: #C84B31;
  --lightpink: #ECDBBA;
}

#app {
  font-family: 'Open Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
}

.sections {
  display: flex;
}

.section {
  min-width: 45vw;
  color: var(--grey);
  height: 100vh;
  padding-right: 45vw;
  margin-left: -45vw;
  -ms-overflow-style: none; /* for Internet Explorer, Edge */
  scrollbar-width: none; /* for Firefox */
  overflow-y: scroll;
}

.section::-webkit-scrollbar {
  display: none;
}

#Home {
  z-index: 0;
  background: var(--blue);
}

.inside {
  box-sizing: border-box;
  padding: 10%;
  text-align: left;
}

#Home {
  margin-left: 0;
}

</style>
