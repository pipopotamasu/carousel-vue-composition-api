<template>
  <svg
    @click="onClick"
    class="arrow"
    width="45"
    height="58"
    viewBox="0 0 45 58"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
  >
    <path :d="d" fill="#C4C4C4" stroke="black" />
  </svg>
</template>

<script lang="ts">
import Vue from 'vue'

export enum Direction {
  left = 1,
  right
}

const LEFT = 'M44.5 56.669L0.932647 29L44.5 1.33102L44.5 56.669Z'
const RIGHT = 'M0.5 1.33102L44.0674 29L0.5 56.669L0.5 1.33102Z'

export default Vue.extend({
  props: {
    direction: {
      type: Number as Vue.PropType<Direction>,
      default: Direction.left
    }
  },
  computed: {
    d (): string {
      return this.direction === Direction.left ? LEFT : RIGHT
    }
  },
  methods: {
    onClick () {
      console.log(5)
      this.$emit('click')
    }
  }
})
</script>

<style lang="scss" scoped>
.arrow {
  cursor: pointer;
}
</style>
