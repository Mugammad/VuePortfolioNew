<template>
  <div class="section" id="Projects" @click="clicked">
      <div class="inside">
            <h1>PROJECTS</h1>
            <div class="line">
            
            </div>
            <div class="header">
                <h4>
                    WHAT I'VE DONE SO FAR
                </h4>
                <p>
                    The Projects I've created since the start of my web dev journey.
                </p>
            </div>
            <div class="cards">
                <div class="loader" v-if="loading">
                    <div class="hollow-dots-spinner">
                      <div class="dot"></div>
                      <div class="dot"></div>
                      <div class="dot"></div>
                    </div>
                </div>
                <div class="card" v-for="(project, index) in projects" :key="project.id">
                    <img :src="project.img" alt="">
                    <div class="middle">
                        <div class="text" @click="toggleModal(index)"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--! Font Awesome Pro 6.0.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path d="M432 256c0 17.69-14.33 32.01-32 32.01H256v144c0 17.69-14.33 31.99-32 31.99s-32-14.3-32-31.99v-144H48c-17.67 0-32-14.32-32-32.01s14.33-31.99 32-31.99H192v-144c0-17.69 14.33-32.01 32-32.01s32 14.32 32 32.01v144h144C417.7 224 432 238.3 432 256z"/></svg></div>
                    </div>
                </div>
            </div>
      </div>
  </div>
</template>

<script>
export default {
    props: [
        'projects',
        'loading'
    ],
    data() {
        return {
            
        }
    },
    methods: {
        clicked() {
            this.$emit('clicked')
        },
        toggleModal(i){
            this.$emit('toggle', i)
        }
    },
    
}
</script>

<style>
    .loader {
        width: fit-content;
        margin: 0 auto;
    }

    #Projects {
        z-index: 4;
        background: var(--black2);
    }

    #Projects .inside .header {
        border: none
    }

    .card img{
        opacity: 1;
        display: block;
        height: 300px;
        width: 100%;
        object-fit: cover;
        transition: .5s ease;
        backface-visibility: hidden;
    }

    .card{
        height: 300px;
        box-sizing: border-box;
        overflow: hidden;
        background: var(--darkgreen);
        margin-bottom: 70px;
    }

    .middle {
        transition: .5s ease;
        opacity: 0;
        height: 300px;
        width: 100%;
        /* top: 50%;
        left: 50%; */
        transform: translate(0, -100%);
        -ms-transform: translate(0, -100%);
        text-align: center;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .card:hover img {
        opacity: 0.3;
    }

    .card:hover .middle {
        opacity: 1;
    }

    .text {
        width: 30%;
        height: fit-content;
        padding: 0;
        gap: 0;
    }

    .text > svg{
        fill: var(--grey);
        cursor: pointer;
    }

    .hollow-dots-spinner, .hollow-dots-spinner * {
      box-sizing: border-box;
    }

    .hollow-dots-spinner {
      height: 15px;
      width: calc(30px * 3);
    }

    .hollow-dots-spinner .dot {
      width: 15px;
      height: 15px;
      margin: 0 calc(15px / 2);
      border: calc(15px / 5) solid var(--darkgreen);
      border-radius: 50%;
      float: left;
      transform: scale(0);
      animation: hollow-dots-spinner-animation 1000ms ease infinite 0ms;
    }

    .hollow-dots-spinner .dot:nth-child(1) {
      animation-delay: calc(300ms * 1);
    }

    .hollow-dots-spinner .dot:nth-child(2) {
      animation-delay: calc(300ms * 2);
    }

    .hollow-dots-spinner .dot:nth-child(3) {
      animation-delay: calc(300ms * 3);

    }

    @keyframes hollow-dots-spinner-animation {
      50% {
        transform: scale(1);
        opacity: 1;
      }
      100% {
        opacity: 0;
      }
    }
    
</style>