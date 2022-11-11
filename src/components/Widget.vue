<script setup>
import { computed } from "vue";

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
  ratioWidth: {
    type: Number,
    default: 1,
  },
  ratioHeight: {
    type: Number,
    default: 1,
  },
  type: {
    type: String,
    default: "", // fixedSize、widthAuto、screenAuto、equalScale
  },
});

const actWidth = computed(() => {
  switch (props.type) {
    case "widthAuto":
    case "screenAuto":
      return props.width * props.ratioWidth;
    default:
      return props.width;
  }
});
const actHeight = computed(() => {
  switch (props.type) {
    case "screenAuto":
      return props.height * props.ratioHeight;
    default:
      return props.height;
  }
});
const actLeft = computed(() => {
  switch (props.type) {
    case "widthAuto":
    case "screenAuto":
      return props.left * props.ratioWidth;
    default:
      return props.left;
  }
});
const actTop = computed(() => {
  switch (props.type) {
    case "screenAuto":
      return props.top * props.ratioHeight;
    default:
      return props.top;
  }
});
</script>

<template>
  <div
    class="widgetBox"
    :style="{
      width: actWidth + 'px',
      height: actHeight + 'px',
      left: actLeft + 'px',
      top: actTop + 'px',
    }"
  >
    <slot></slot>
  </div>
</template>

<style scoped>
.widgetBox {
  position: absolute;
  overflow: hidden;
}
</style>
