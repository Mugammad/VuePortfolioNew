<template>
    <div class="nav v-scroll-spy-active v-scroll-spy-link" :id="navId">
        <a @click="hideNav" v-for="section of sections" :key="section.id" :href="section.id">{{ section.name }}</a>
    </div>
</template>

<script>
export default {
    props:[
        'navId'
    ],
    data() {
        return {
            sections: [
                {name: 'Home', id: '#Home' },
                {name: 'About', id: '#About' },
                {name: 'Experience', id: '#Experience' },
                {name: 'Skills', id: '#Skills' },
                {name: 'Projects', id: '#Projects' },
                {name: 'Testimonials', id: '#Testimonials' },
                {name: 'Contact', id: '#Contact' },
            ],
        }
    },
    methods: {
        hideNav() {
            this.$emit('hideNav')
        }
    },
}
</script>

<style>
*{
    margin: 0;
    scroll-behavior: smooth;
    overflow-x: hidden;
}
.nav {
    min-width: 10vw;
    background: var(--black);
    top: 0;
    height: 100vh;
    box-sizing: border-box;
    position: sticky;
    padding: 20px;
}
.nav {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 0;
}
a{
    text-decoration: none;
    text-decoration: none;
    cursor: pointer;
    color: var(--grey);
    display: inline-block;
}

.nav a {
    padding: 5px 10px;
    padding: 10px 0px;
    padding-left: 0;
    font-size: 16px;
    width: 100%;
    border-bottom: 0.5px solid rgba(241, 250, 238, 0.5);
}

a:hover {
  color: var(--darkgreen);
  transition: 0.2s linear;
}
</style>