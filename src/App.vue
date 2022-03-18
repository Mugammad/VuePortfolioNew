<template>
  <div id="app">
    <Nav :navId="'navDesktop'"/>
    <transition name="slideIn" mode="in-out">
      <Nav :navId="'navMobile'" v-if="this.showNav" @hideNav="hideNav"/>
    </transition>
    <transition name="fade" mode="in-out">
      <div class="navMobileBg" v-if="this.showNav"></div>
    </transition>
      <div class="navBtn" @click="toggleNav">
        <transition name="fade" mode="in-out">
          <svg v-if="!this.showNav" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--! Font Awesome Pro 6.0.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path d="M0 96C0 78.33 14.33 64 32 64H416C433.7 64 448 78.33 448 96C448 113.7 433.7 128 416 128H32C14.33 128 0 113.7 0 96zM0 256C0 238.3 14.33 224 32 224H416C433.7 224 448 238.3 448 256C448 273.7 433.7 288 416 288H32C14.33 288 0 273.7 0 256zM416 448H32C14.33 448 0 433.7 0 416C0 398.3 14.33 384 32 384H416C433.7 384 448 398.3 448 416C448 433.7 433.7 448 416 448z"/></svg>
        </transition>
        <transition name="fade" mode="in-out">
          <svg v-if="this.showNav" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 320 512"><!--! Font Awesome Pro 6.0.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path d="M310.6 361.4c12.5 12.5 12.5 32.75 0 45.25C304.4 412.9 296.2 416 288 416s-16.38-3.125-22.62-9.375L160 301.3L54.63 406.6C48.38 412.9 40.19 416 32 416S15.63 412.9 9.375 406.6c-12.5-12.5-12.5-32.75 0-45.25l105.4-105.4L9.375 150.6c-12.5-12.5-12.5-32.75 0-45.25s32.75-12.5 45.25 0L160 210.8l105.4-105.4c12.5-12.5 32.75-12.5 45.25 0s12.5 32.75 0 45.25l-105.4 105.4L310.6 361.4z"/></svg>
        </transition>
    </div>
    <div class="nav2"></div>
    <div class="sections v-scroll-spy">
      <Landing/>
      <About @clicked="scroll('About')" />
      <Experience @clicked="scroll('Experience')"/>
      <Skills @clicked="scroll('Skills')"/>
      <Projects @clicked="scroll('Projects')" :projects="projects" @toggle="toggleModal" :loading="loading"/>
      <Testimonials @clicked="scroll('Testimonials')" :testimonials="this.testimonials" :loading="loading"/>
      <Contact @clicked="scroll('Contact')"/>
      <div v-for="(project, index) in projects" :key="project.id">
        <transition name="fade3" mode="in-out">
          <Modal :header="project.title" :image="project.img" :desc="project.description" :netlify="project.netlify" :github="project.github" v-if="project.showModal" @clicked="toggleModal(index)"/>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import Landing from './Sections/Landing.vue'
import About from './Sections/About.vue'
import Experience from './Sections/Experience.vue'
import Projects from './Sections/Projects.vue'
import Contact from './Sections/Contact.vue'
import Skills from './Sections/Skills.vue'
import Modal from './components/Modal.vue'
import Nav from './components/Nav.vue'
import Testimonials from './Sections/Testimonials.vue'
export default {
  name: 'App',
  components: {
    Landing,
    About,
    Experience,
    Projects,
    Contact,
    Skills,
    Modal,
    Nav,
    Testimonials,
  },

  data() {
    return {
      projects: [],
      testimonials: [],
      loading: false,
      showNav: false
    }
  },
  methods: {
      scroll(id) {
      let screenSize = window.matchMedia("(max-width: 685px)")
      if (screenSize.matches) { // If media query matches
        console.log('srollTo disabled');
      } else {
        document.getElementById(id).scrollIntoView({
          behavior: "smooth"
        });
      }
    },
    toggleModal(i){
      this.projects[i].showModal = !this.projects[i].showModal
    },
    toggleNav(){
      this.showNav = !this.showNav
    },
    hideNav(){
      this.showNav = false
    }
  },
  computed: {
    navChanger(){
      $(document).ready(function(){
        $(window).scroll(function(){
  	      var scroll = $(window).scrollTop();
	        if (scroll > 300) {
	          $(".nav2").css("opacity" , "1");
	        }

	        else{
		        $(".nav2").css("opacity" , "0");  	
	        }
        })
      })
    }
  },
  mounted() {
        this.loading = true
        fetch('https://portfolio-backend-mugammad.herokuapp.com/projects')
        .then(res => res.json())
        .then(data => {
            data.projects.forEach(project => {
                this.projects.push({...project, showModal: false})
            });
            this.loading = false
        })
    },

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
  background: var(--black);
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

.header {
  padding: 70px 0;
  border-bottom: 0.1px solid var(--grey);
}

.header p {
  margin-top: 1rem;
}

.fade3-enter-active,
.fade3-leave-active {
  transition: opacity 0.3s;
}
.fade3-enter{
  opacity: 0;
}
.fade3-leave-to{
  opacity: 0;
}

.slideIn-enter-active,
.slideIn-leave-active {
  transition: transform 0.3s;
}
.slideIn-enter{
  transform: translateX(-100%);
}
.slideIn-leave-to{
  transform: translateX(-100%);
}

.fade-enter,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter-from{
  opacity: 0;
}
.fade-leave-to{
  opacity: 0;
}

.navBtn {
  display: none;
}

.nav2 {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 80px;
  background: var(--black);
  opacity: 0;
}

@media screen and (max-width: 1325px){
  .section {
  min-width: 80vw;
  color: var(--grey);
  height: 100vh;
  padding-right: 0;
  margin-left: 0;
}

.nav {
    min-width: 20vw;
    background: var(--black);
    top: 0;
    height: 100vh;
    box-sizing: border-box;
    position: sticky;
    padding: 20px;
}
}

@media screen and (max-width: 685px){
  .grid{
    display: block;
  }

  .grid-1{
    margin-bottom: 1rem;
  }

  .navBtn {
    display: block;
  }
  #navDesktop {
    display: none;
  }

  #app{
    display: block;
  }

  .sections {
    display: block;
  }

  .section {
  min-width: 100vw;
  color: var(--grey);
  height: fit-content;
  padding-top: 50px;
  padding-right: 0;
  margin-left: 0;
}

#Home {
  padding-top: 0;
  height: 100vh;
}

.nav {
    position: fixed;
    min-width: 40vw;
    background: var(--black);
    top: 0;
    height: 100vh;
    box-sizing: border-box;
    padding: 20px;
    z-index: 100;
}
}

.navMobileBg {
  width: 100vh;
  height: 100vh;
  position: fixed;
  background: black;
  opacity: 0.4;
}

.navBtn {
  position: fixed;
  width: 50px;
  height: fit-content;
  top: 16px;
  left: 20px;
  z-index: 101;
}

.navBtn svg {
  fill: var(--darkgreen);
  position: fixed;
  width: 50px;
  height: 50px;
}
</style>
