<script setup>
import { onMounted, ref } from "vue";
import * as echarts from "echarts";
import ResizeObserver from "resize-observer-polyfill";

const chartBox = ref(null);
onMounted(() => {
  let myChart = echarts.init(chartBox.value);
  let option;

  option = {
    tooltip: {
      trigger: "item",
    },
    series: [
      {
        name: "Access From",
        type: "pie",
        radius: ["40%", "70%"],
        avoidLabelOverlap: false,
        itemStyle: {
          borderRadius: 10,
          borderColor: "#fff",
          borderWidth: 2,
        },
        label: {
          show: false,
          position: "center",
        },
        emphasis: {
          label: {
            show: true,
            fontSize: "40",
            fontWeight: "bold",
          },
        },
        labelLine: {
          show: false,
        },
        data: [
          { value: 1048, name: "Search Engine" },
          { value: 735, name: "Direct" },
          { value: 580, name: "Email" },
          { value: 484, name: "Union Ads" },
          { value: 300, name: "Video Ads" },
        ],
      },
    ],
  };

  option && myChart.setOption(option);

  const ro = new ResizeObserver(() => {
    myChart.resize();
  });
  ro.observe(chartBox.value);
});
</script>

<template>
  <div class="chartBox" ref="chartBox"></div>
</template>

<style scoped>
.chartBox {
  width: 100%;
  height: 100%;
}
</style>
