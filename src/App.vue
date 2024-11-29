<template>
  <div id="app">
    <HeightData ref="heightData"></HeightData>
    <HeightChart :heightData="heightData"></HeightChart>
  </div>
</template>

<script>
import HeightData from './components/HeightData.vue';
import HeightChart from './components/HeightChart.vue';
export default {
  components: {
    HeightData,
    HeightChart
  },
  data() {
    return {
      heightData: []
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.heightData = this.$refs.heightData.heightData;
    });
  }
};
</script>