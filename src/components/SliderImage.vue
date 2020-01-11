<template>
  <img
    :src="image.src"
    :alt="image.alt"
    class="slider-image"
    :class="{ 'slider-image-active': active }"
  />
</template>

<script lang="ts">
import Vue from 'vue'

export type SliderImageType = {
  src: string,
  alt: string
}

export default Vue.extend({
  props: {
    image: {
      type: Object as Vue.PropType<SliderImageType>,
      required: true
    },
    active: {
      type: Boolean,
      required: true
    }
  }
})
</script>

<style lang="scss" scoped>
.slider-image {
  display: none;
  width: 540px;
  height: 300px;
  margin: 0 20px;
}

.slider-image-active {
  display: inline;
}
</style>
