<template>
  <div @click="backToTop()" class="back-to-wrapper">
    <img src="../assets/images/arrows.png" alt="" />
  </div>
</template>

<script>
export default {
  methods: {
    backToTop() {
      window.scrollTo(0, 0)
    }
  }
}
</script>

<style lang="scss">
.back-to-wrapper {
  width: 50px;
  cursor: pointer;
  transition: scale 0.2s ease-out;

  img {
    width: 100%;
  }

  &:hover {
    scale: 1.1;
  }
}
</style>
