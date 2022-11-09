<script setup>
import { onMounted, ref } from "vue";
import * as echarts from "echarts";

const chartBox = ref(null);
onMounted(() => {
  let myChart = echarts.init(chartBox.value);
  let option;

  option = {
    xAxis: {
      type: "category",
      data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
    },
    yAxis: {
      type: "value",
    },
    series: [
      {
        data: [120, 200, 150, 80, 70, 110, 130],
        type: "bar",
        showBackground: true,
        backgroundStyle: {
          color: "rgba(180, 180, 180, 0.2)",
        },
      },
    ],
  };

  option && myChart.setOption(option);
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
