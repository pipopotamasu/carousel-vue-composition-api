<template>
  <div class="carousel-container">
    <div class="slider">
      <div class="arrow-wrapper">
        <DefaultArrow :direction="arrowDirectionLeft" />
      </div>
      <SliderImage
        v-for="(image, i) in images"
        :key="i"
        :image="image"
        :active="0 === i"
      />
      <div class="arrow-wrapper">
        <DefaultArrow :direction="arrowDirectionRight" />
      </div>
    </div>
    <ul class="indicator-list">
      <CarouselIndicator
        v-for="(image, i) in images"
        :key="i"
        :active="0 === i"
      />
    </ul>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import DefaultArrow, { Direction as ArrowDirection } from './DefaultArrow.vue'
import SliderImage, { SliderImageType } from './SliderImage.vue'
import CarouselIndicator from './CarouselIndicator.vue'

export default Vue.extend({
  props: {
    images: {
      type: Array as Vue.PropType<SliderImageType[]>,
      required: true
    }
  },
  components: {
    DefaultArrow,
    SliderImage,
    CarouselIndicator
  },
  computed: {
    arrowDirectionLeft () {
      return ArrowDirection.left
    },
    arrowDirectionRight () {
      return ArrowDirection.right
    }
  }
})
</script>

<style lang="scss" scoped>
.carousel-container {
  width: 800px;

  .slider {
    display: flex;
    justify-content: center;

    .arrow-wrapper {
      margin: auto 0;
    }
  }

  .indicator-list {
    display: flex;
    justify-content: center;
    list-style:none;
    padding-inline-start: 0;
  }
}
</style>
