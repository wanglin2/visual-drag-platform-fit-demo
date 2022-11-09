<script setup>
const props = defineProps({
  width: {
    type: Number,
    default: 0,
  },
  height: {
    type: Number,
    default: 0,
  },
  left: {
    type: Number,
    default: 0,
  },
  top: {
    type: Number,
    default: 0,
  },
});
</script>

<template>
  <div
    class="widgetBox"
    :style="{
      width: width + 'px',
      height: height + 'px',
      left: left + 'px',
      top: top + 'px',
    }"
  >
    <slot></slot>
  </div>
</template>

<style scoped>
.widgetBox {
  position: absolute;
}
</style>
