<template>
    <div class="nav" :id="navId">
        <a :class="[anchor == section.name && !isGrey ? 'activeAnchor' : '', anchor == section.name && isGrey ? 'activeAnchorGrey' : '', anchor != section.name ? 'unactiveNav' : '']" @click="hideNav(section.id)" v-for="section of sections" :key="section.id" :href="section.id" >{{ section.name }}</a>
    </div>
</template>

<script>
export default {
    props:[
        'navId',
        'isGrey',
        'sections',
        'anchor'
    ],
    data() {
        return {
        }
    },
    methods: {
        hideNav(section) {
            this.$emit('hideNav')
            this.$emit('changeNav', section)
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


.greyNav {
    min-width: 10vw;
    background: var(--black2);
    top: 0;
    height: 100vh;
    box-sizing: border-box;
    position: sticky;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 0;
    transition: 0.3s;
}

.nav {
    min-width: 10vw;
    background: var(--black);
    top: 0;
    height: 100vh;
    box-sizing: border-box;
    position: sticky;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 0;
    transition: 0.3s;
}

a{
    text-decoration: none;
    text-decoration: none;
    cursor: pointer;
    color: var(--grey);
    display: inline-block;
}

.unactiveNav {
    padding: 5px 10px;
    padding: 10px 0px;
    padding-left: 0;
    font-size: 16px;
    width: 100%;
    transition: 0.3s;
}

a:hover {
  color: var(--darkgreen);
  transition: 0.2s linear;
}

.activeAnchor{
    margin: 10px 0px;
    padding-left: 10px;
    font-size: 16px;
    width: 100%;
    border-left: 2px solid var(--darkgreen);
    transition: 0.3s;
}

.activeAnchorGrey{
    margin: 10px 0px;
    padding-left: 10px;
    font-size: 16px;
    width: 100%;
    border-left: 2px solid var(--darkgreen);
    transition: 0.3s;
}
</style>