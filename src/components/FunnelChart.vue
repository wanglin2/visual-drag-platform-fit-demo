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
      formatter: "{a} <br/>{b} : {c}%",
    },
    legend: {
      show: false,
    },
    series: [
      {
        name: "Funnel",
        type: "funnel",
        left: "10%",
        top: 60,
        bottom: 60,
        width: "80%",
        min: 0,
        max: 100,
        minSize: "0%",
        maxSize: "100%",
        sort: "descending",
        gap: 2,
        label: {
          show: true,
          position: "inside",
        },
        labelLine: {
          length: 10,
          lineStyle: {
            width: 1,
            type: "solid",
          },
        },
        itemStyle: {
          borderColor: "#fff",
          borderWidth: 1,
        },
        emphasis: {
          label: {
            fontSize: 20,
          },
        },
        data: [
          { value: 60, name: "Visit" },
          { value: 40, name: "Inquiry" },
          { value: 20, name: "Order" },
          { value: 80, name: "Click" },
          { value: 100, name: "Show" },
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
