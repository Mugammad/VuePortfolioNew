<template>
  <div class="section" id="Skills" @click="clicked">
        <div class="inside container p-5">
            <h1 class="mb-3 ">SKILLS</h1>
            <div class="line">
            
            </div>
            <div class="header">
                <h4>
                    SUCH SKILL, MUCH WOW, VERY COMPUTER
                </h4>
                <p>
                    Check out the skills i have gained so far. I am far from where I want to be but I am proud of what I have accomplished.
                </p>
            </div>
            <div class="skillIcons">
                <div v-for="skill in skills" :key="skill.id" class="skillIcon">
                    <i :class="skill.icon"></i>
                </div>
            </div>
        </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            skills: [
                { id: 1, icon: 'devicon-css3-plain'},
                { id: 2, icon: 'devicon-html5-plain'},
                { id: 3, icon: 'devicon-javascript-plain'},
                { id: 4, icon: 'devicon-bootstrap-plain'},
                { id: 5, icon: 'devicon-python-plain'},
                { id: 6, icon: 'devicon-vuejs-plain'},
                { id: 7, icon: 'devicon-nodejs-plain'},
                { id: 8, icon: 'devicon-mysql-plain'},
            ]
        }
    },
    methods: {
        clicked() {
            this.$emit('clicked')
        }
    },
}
</script>

<style>
    #Skills {
        z-index: 3;
        background: var(--black);
    }

    .skillIcons {
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 20px;
        padding: 70px 0;
        border-bottom: 0.1px solid var(--grey);
    }

    .skillIcon {
        min-width: 150px;
        height: fit-content;
        font-size: 4rem;
        color: var(--grey);
        display: flex;
        text-align: center;
        justify-content: center;
        flex-direction: column;
    }
</style>