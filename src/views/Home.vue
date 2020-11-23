<template>
  <div id="mountNode" style="background-color: #2c3e50"></div>
</template>

<script>
import { Chart } from '@antv/g2';

export default {
  name: 'Home',
  data() {
    return {
      data: [
        { year: '1951 年',type:'avg', sales: 38 },
        { year: '1952 年',type:'avg', sales: 52 },
        { year: '1956 年',type:'avg', sales: 61 },
        { year: '1957 年',type:'avg', sales: 145 },
        { year: '1958 年',type:'self', sales: 48 },
        { year: '1959 年',type:'avg', sales: 38 },
        { year: '1960 年',type:'self', sales: 38 },
        { year: '1962 年',type:'self', sales: 38 },
      ]
    }
  },
  mounted() {
    this.init()
  },
  methods: {
    init() {
      const chart = new Chart({
        container: 'mountNode',
        autoFit: false,
        width: 400,
        height: 300,
      });

      chart.data(this.data);
      chart.scale('sales', {
        alias: ' ',
      });
      chart.axis('sales', {
        title: {},
      });
      chart.legend({
        position: 'top-left',
        style: {

        }
      });
      chart.line().position('year*sales')
          .color('type')
          .shape('slice-shape');
      chart.point().position('year*sales')
          .color('type')
          .shape('circle');

      chart.render();
    }
  }
}
</script>
