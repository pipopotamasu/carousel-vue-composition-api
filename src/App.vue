<template>
  <div id="app">
    <MyCarousel :images="images" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import MyCarousel from './components/MyCarousel.vue'

export default Vue.extend({
  components: {
    MyCarousel
  },
  computed: {
    images () {
      return [
        { src: './sample1.png', alt: '1' },
        { src: './sample2.png', alt: '2' },
        { src: './sample3.png', alt: '3' }
      ]
    }
  }
})
</script>

<style>
#app {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
