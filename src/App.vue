<script setup>
import { ref } from "vue";
import Widget from "./components/Widget.vue";
import LineChart from "./components/LineChart.vue";
import BarChart from "./components/BarChart.vue";
import PieChart from "./components/PieChart.vue";
import FunnelChart from "./components/FunnelChart.vue";

// 1280*720、1920*1080
const canvasWidth = ref(1920);
const canvasHeight = ref(1080);
const originCanvasWidth = ref(canvasWidth.value);
const originCanvasHeight = ref(canvasHeight.value);
const widgetWidth = ref(960);
const widgetHeight = ref(540);

window.addEventListener("resize", () => {
  let windowWidth = window.innerWidth;
  let windowHeight = window.innerHeight;
});
</script>

<template>
  <div class="canvasBox">
    <div
      class="canvas"
      :style="{ width: canvasWidth + 'px', height: canvasHeight + 'px' }"
    >
      <Widget :width="960" :height="540" :left="0" :top="0">
        <LineChart></LineChart>
      </Widget>
      <Widget :width="960" :height="540" :left="960" :top="0">
        <BarChart></BarChart>
      </Widget>
      <Widget :width="960" :height="540" :left="0" :top="540">
        <PieChart></PieChart>
      </Widget>
      <Widget :width="960" :height="540" :left="960" :top="540">
        <FunnelChart></FunnelChart>
      </Widget>
    </div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}
</style>
<style scoped>
.canvasBox {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.canvas {
  position: relative;
}
</style>
