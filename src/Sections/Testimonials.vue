<template>
    <div class="section" id="Testimonials" @click="clicked">
        <div class="inside">
            <div>
                <h1>TESTIMONIALS</h1>
                <div class="line"></div>
            </div>
            <div class="header testHeader">
                <h4>
                    ASK MY COLLEAGUES
                </h4>
                <p>
                    I've already told you a little about myself but... what do the people say?
                </p>
            </div>
            <div class="loader" v-if="loading">
                <div class="hollow-dots-spinner">
                  <div class="dot"></div>
                  <div class="dot"></div>
                  <div class="dot"></div>
                </div>
            </div>
            <div class="Quotes" v-for="(testimonial, i) in testimonials" :key="testimonial.id">
            <transition name="fade" mode="in-out">
            <div class="flexContainer" v-if="testimonial.show">
                <div class="quoteBox">
                    <div class="quoteOpen">
                        <svg xmlns="http://www.w3.org/2000/svg" width="15%" height="15%" fill="currentColor" class="bi bi-quote" viewBox="0 0 16 16">
                            <path d="M12 12a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1h-1.388c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 9 7.558V11a1 1 0 0 0 1 1h2Zm-6 0a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1H4.612c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 3 7.558V11a1 1 0 0 0 1 1h2Z"/>
                        </svg>
                    </div>
                    <div class="quote" >
                        <h3>{{ testimonial.testimonial }}</h3>
                    </div>
                    <div class="quoteClose">
                        <svg xmlns="http://www.w3.org/2000/svg" width="15%" height="15%" fill="currentColor" class="bi bi-quote" viewBox="0 0 16 16">
                            <path d="M12 12a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1h-1.388c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 9 7.558V11a1 1 0 0 0 1 1h2Zm-6 0a1 1 0 0 0 1-1V8.558a1 1 0 0 0-1-1H4.612c0-.351.021-.703.062-1.054.062-.372.166-.703.31-.992.145-.29.331-.517.559-.683.227-.186.516-.279.868-.279V3c-.579 0-1.085.124-1.52.372a3.322 3.322 0 0 0-1.085.992 4.92 4.92 0 0 0-.62 1.458A7.712 7.712 0 0 0 3 7.558V11a1 1 0 0 0 1 1h2Z"/>
                        </svg>
                    </div>
                    <div class="quoteFooter">
                        <img :src="testimonial.img" alt="">
                        <div class="personInfo">
                            <h2>{{ testimonial.name.toUpperCase() }}</h2>
                            <h3>{{ testimonial.relationship.toUpperCase() }}</h3>
                        </div>
                    </div>
                </div>
                <div class="arrow">
                    <div class="push"></div>
                    <svg @click="next(i)" xmlns="http://www.w3.org/2000/svg" width="50" height="50" fill="currentColor" class="bi bi-arrow-right" viewBox="0 0 16 16">
                        <path fill-rule="evenodd" d="M1 8a.5.5 0 0 1 .5-.5h11.793l-3.147-3.146a.5.5 0 0 1 .708-.708l4 4a.5.5 0 0 1 0 .708l-4 4a.5.5 0 0 1-.708-.708L13.293 8.5H1.5A.5.5 0 0 1 1 8z"/>
                    </svg>
                </div>
            </div>
            </transition>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: [
        'loading'
    ],
    data() {
        return {
            testimonials: [],
            index: null,
        }
    },
    methods: {
      clicked() {
        this.$emit('clicked')
    },
    next(position) {
        this.testimonials[position].show = false
        if(position == this.testimonials.length -1){
            this.index = 0
        }else{
            this.index = position + 1
        }
        this.testimonials[this.index].show = true
    }
  },
  mounted() {
    fetch('https://portfolio-backend-mugammad.herokuapp.com/testimonials')
        .then(res => res.json())
        .then(data => {
            data.testimonials.forEach(element => {
                this.testimonials.push({...element, show: false})
                this.testimonials[0].show = true
            });
        })
  },
}
</script>

<style>
    .inside {
        min-height: 100vh;
    }
    
    .Quotes {
        width: 100%;
    }
    .arrow {
        display: flex;
        padding-top: 2rem;
    }
    .arrow svg{
        cursor: pointer;
        opacity: 0.5;
        transition: 0.3s;
    }
    .arrow svg:hover{
        opacity: 1;
        transition: 0.3s;
    }
    .push {
        width: 100%;
    }
    .flexContainer {
        width: 100%;
    }

    .quoteBox {
        width: 100%;
    }

    .quoteFooter {
        padding: 0 15%;
        display: flex;
    }

    .quoteFooter img {
        margin-right: 2rem;
        width: 60px;
        height: 60px;
        border-radius: 50%;
    }

    .personInfo {
        display: flex;
        flex-direction: column;
    }

    .personInfo h3 {
        opacity: 0.3;
    }

    .quoteClose {
        transform: rotate(180deg);
    }

    .quoteClose, .quoteOpen {
        opacity: 0.3;
        color: var(--darkgreen);
    }

    .quote {
        opacity: 0.5;
        padding: 0 15%;
        box-sizing: border-box;
    }

    #Testimonials {
        z-index: 5;
        background: var(--black);
    }

    .testHeader{
        border-bottom: none !important;
    }
</style>