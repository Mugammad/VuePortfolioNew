<template>
  <div class="modal">
      <div class="backdrop">
        <div class="content">
            <h1>{{ header }}</h1>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  props: [
    'header'
  ]
}
</script>

<style>
  .backdrop {
    background: rgba(0, 0, 0, 0.6);
    display: flex;
    justify-content: center;
    flex-direction: column;
    position: absolute;
    width: 100%;
    height: 100vh;
    z-index: 6;
    top: 0;
    left: 0;
  }

  .content {
    max-width: 700px;
    height: 80vh;
    margin: 0 auto;
    background: var(--black2);
    top: 0;
    left: 0;
  }
</style>