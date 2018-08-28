<template>
 <div>
   <svg></svg>
 </div>
</template>

<script>
 const color = '#313131';
 import * as d3 from 'd3';
 export default {
  name: 'SkillChart',

  data() {
   return {
    svg: '',
   }
  },

  computed: {
  },
  mounted() {
   this.setupD3();
   this.drawCircle(300, 100, 10, color)

  },
  methods: {
   drawAxes() {

   },
   setupD3() {
    this.svg = d3.select('svg');
    const svg = this.svg;
    svg.append('g').attr('class', 'container');
    svg.on('click', function() {
      const drawCircle = (cx, cy, r, color) => {
        svg.select('.container')
         .append('circle')
         .attr('cx', cx)
         .attr('cy', cy)
         .attr('r', r)
         .attr('fill', color);
    }
     const coords = d3.mouse(this);
     drawCircle(coords[0], coords[1], 10, color);
    })
   },
   drawCircle(cx, cy, r, color) {
    this.svg.select('.container')
     .append('circle')
     .attr('cx', cx)
     .attr('cy', cy)
     .attr('r', r)
     .attr('fill', color);
   },

  }
 }

</script>

<style scoped>
svg {
 height: 500px;
 width: 600px;
}
</style>