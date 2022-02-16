<template>
  <div class="modal">
      <div class="backdrop" @click.self="toggleModal">
          <div class="content">
              <h1>{{ header.toUpperCase() }}</h1>
              <div class="line"></div>
              <div class="imgdiv">
                <img :src="image" alt="">
              </div>
              <p>{{ desc }}</p>
          </div>
      </div>
  </div>
</template>

<script>
export default {
  props: [
    'header',
    'image',
    'desc'
  ],

  data() {
    return {
      ShowModal: false
    }
  },
  methods: {
    toggleModal(){
      this.$emit('clicked')
      this.ShoModal = !this.ShoModal
    }
  },
  mounted() {
    this.ShoModal = !this.ShoModal
  },
}
</script>

<style>

  .modal {
    position: absolute;
    width: 100%;
    height: 100vh;
    z-index: 6;
    top: 0;
    left: 0;
  }
  .backdrop {
    background: rgba(0, 0, 0, 0.6);
    display: flex;
    align-items: center;
    width: 100%;
    height: 100vh;
  }

  .content {
    width: 90%;
    max-width: 700px;
    height: 80vh;
    margin: 0 auto;
    padding: 2rem;
    background: var(--black2);
    box-sizing: border-box;
    color: var(--grey);
  }

  .content .line {
    width: 100%;
  }

  .imgdiv {
    height: 200px;
    width: 100%;
    overflow: hidden;
    box-sizing: border-box;
    margin: 2rem 0;
  }

  .imgdiv img {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }
</style>