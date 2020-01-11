<template>
  <li
    class="indicator"
    :class="{ 'indicator-active': active }"
  >

  </li>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: {
    active: {
      type: Boolean,
      required: true
    }
  }
})
</script>

<style lang="scss" scoped>
.indicator {
  width: 30px;
  height: 30px;
  border: 1px black solid;
  background-color: white;
  border-radius: 50%;
  margin-right: 10px;
  cursor: pointer;
  &:hover {
    background-color: black;
  }
}

.indicator-active {
  background-color: black;
}
</style>
