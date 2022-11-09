<script setup>
import { ref } from "vue";
import Widget from "./components/Widget.vue";
import LineChart from "./components/LineChart.vue";
import BarChart from "./components/BarChart.vue";
import PieChart from "./components/PieChart.vue";
import FunnelChart from "./components/FunnelChart.vue";

const canvasWidth = ref(1080);
const canvasHeight = ref(720);
const widgetWidth = ref(540);
const widgetHeight = ref(360);

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
      <Widget :width="540" :height="360" :left="0" :top="0">
        <LineChart></LineChart>
      </Widget>
      <Widget :width="540" :height="360" :left="540" :top="0">
        <BarChart></BarChart>
      </Widget>
      <Widget :width="540" :height="360" :left="0" :top="360">
        <PieChart></PieChart>
      </Widget>
      <Widget :width="540" :height="360" :left="540" :top="360">
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
