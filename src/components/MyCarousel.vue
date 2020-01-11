<template>
  <div class="carousel-container">
    <div class="slider">
      <div class="arrow-wrapper">
        <DefaultArrow
          @click="onClickArrow(arrowDirectionLeft)"
          :direction="arrowDirectionLeft"
        />
      </div>
      <SliderImage
        v-for="(image, i) in images"
        :key="i"
        :image="image"
        :active="i === state.activeIndex"
      />
      <div class="arrow-wrapper">
        <DefaultArrow
          @click="onClickArrow(arrowDirectionRight)"
          :direction="arrowDirectionRight"
        />
      </div>
    </div>
    <ul class="indicator-list">
      <CarouselIndicator
        v-for="(image, i) in images"
        @click.native="onClickIndicator(i)"
        :key="i"
        :active="i === state.activeIndex"
      />
    </ul>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import DefaultArrow, { Direction as ArrowDirection } from './DefaultArrow.vue'
import { createComponent, computed, reactive } from '@vue/composition-api'
import SliderImage, { SliderImageType } from './SliderImage.vue'
import CarouselIndicator from './CarouselIndicator.vue'

function arrowDirectionComposition () {
  const arrowDirectionLeft = computed((): ArrowDirection => ArrowDirection.left)
  const arrowDirectionRight = computed((): ArrowDirection => ArrowDirection.right)

  return { arrowDirectionLeft, arrowDirectionRight }
}

function activeImageComposition (images: SliderImageType[]) {
  const state = reactive<{ activeIndex: number }>({
    activeIndex: 0
  })

  function onClickIndicator (i: number) {
    state.activeIndex = i
  }

  function onClickArrow (direction: ArrowDirection) {
    const activeIndex = state.activeIndex
    if (direction === ArrowDirection.left) {
      state.activeIndex = activeIndex === 0 ? images.length - 1 : activeIndex - 1
    } else {
      state.activeIndex = activeIndex === images.length - 1 ? 0 : activeIndex + 1
    }
  }

  return {
    state,
    onClickIndicator,
    onClickArrow
  }
}

export default createComponent({
  props: {
    images: {
      type: Array,
      required: true
    }
  },
  components: {
    DefaultArrow,
    SliderImage,
    CarouselIndicator
  },
  setup (props: { images: SliderImageType[] }) {
    return {
      ...activeImageComposition(props.images),
      ...arrowDirectionComposition()
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
