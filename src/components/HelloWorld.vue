<template>
<div class="world">
  <grid-layout class="grid-layout" :layout="layout" :col-num="2" :row-height="rowHeight" :is-draggable="true" :is-resizable="false" :is-mirrored="false" :vertical-compact="true" :margin="[10, 10]" :use-css-transforms="true" ref="gridLayout">
    <grid-item v-for="item in layout" :x="item.x" :y="item.y" :w="item.w" :h="item.h" :i="item.i">
      <chart :data="item" @updateLayout="updateLayout" :ref="'chart_'+item.i"></chart>
    </grid-item>
  </grid-layout>
</div>
</template>

<script>
import Chart from './Chart'
import {
  GridLayout,
  GridItem
} from 'vue-grid-layout'

var testLayout = [{
    "x": 0,
    "y": 0,
    "w": 1,
    "h": 0,
    "i": "0",
    content: '东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾地方啦时间段垃圾地方啦时间段'
  },
  {
    "x": 1,
    "y": 0,
    "w": 1,
    "h": 0,
    "i": "1",
    content: '东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾地方啦时间段'
  },
  {
    "x": 0,
    "y": 1,
    "w": 1,
    "h": 0,
    "i": "2",
    content: '东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾地方啦时间段东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾地方啦时间段法拉时间的反垃圾地方啦时间段'
  },
  {
    "x": 1,
    "y": 1,
    "w": 1,
    "h": 0,
    "i": "3",
    content: '东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾地方啦时间段'
  },
  {
    "x": 0,
    "y": 2,
    "w": 1,
    "h": 0,
    "i": "4",
    content: '东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾地方啦时间段东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾地方啦时间段东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾地方啦时间段地方啦时间段东风科技阿隆索打飞机啊垃圾；阿凡涉及地方；安静的法拉时间的反垃圾地方啦时间段'
  }
];
export default {
  name: 'HelloWorld',
  components: {
    GridLayout,
    GridItem,
    Chart
  },
  watch: {},
  methods: {
    updateLayout() {
      this.chartNum++;
      if (this.layout.length != this.chartNum) {
        return;
      }
      this.layout.forEach((item) => {
        let chartHeight = this.$refs['chart_' + item.i][0].$el.scrollHeight;
        console.log(chartHeight)
        let h = Math.ceil(chartHeight / this.rowHeight);
        item.h = h;
      });
      this.$refs.gridLayout.layoutUpdate();
      this.layout.forEach((item) => {
        console.log('-------> \t%s', item.i + '__' + item.h)
      })
    }
  },
  mounted() {
    this.layout = testLayout;
    console.log('hell world mounted')
  },
  data() {
    return {
      layout: [],
      rowHeight: 20,
      chartNum: 0
    }
  }
}
</script>

<style>
.world {
  width: 100%;
}

.grid-layout {
  cursor: default;
}
</style>
