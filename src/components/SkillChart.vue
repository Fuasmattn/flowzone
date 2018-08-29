<template>
 <div>
   <h2>{{skill}}</h2>
   <svg @click="handleClick"></svg>
 </div>
</template>

<script>
 const color = '#313131';
 import * as d3 from 'd3';
 export default {
  name: 'SkillChart',

  data() {
   return {
    index: 0,
    skillStack: ['Scrum', 'MongoDB', 'Angular', 'React-Native', 'Vue', 'Springboot', 'Payara', 'Kubernetes' ],
    skillColors: [],
    svg: '',
   }
  },

  computed: {
   skill() {
    return this.skillStack[this.index];
   }
  },
  mounted() {
   this.setupD3();
  },
  methods: {
   next() {
    if(this.index !== this.skillStack.length - 1) {
     this.index++; return true;
    }
    return false;  
   },
   drawAxes() {

   },
   handleClick() {
    this.next();

   },
   setupD3() {
    this.svg = d3.select('svg');
    const svg = this.svg;
    svg.append('g').attr('class', 'container');
    this.next() && svg.on('click', function() {
      const drawCross = (x, y, r, color) => {
       svg.select('.container')
        .append('line')
        .attr('x1', x - r)
        .attr('x2', x + r )
        .attr('y1', y - r)
        .attr('stroke-width', '3px')
        .attr('y2', y + r);

        svg.select('.container')
        .attr('stroke', color)
        .append('line')
        .attr('x1', x + r)
        .attr('x2', x - r )
        .attr('y1', y - r)
        .attr('y2', y + r)
        .attr('stroke-width', '3px')
        .attr('stroke', color);
    }
     const coords = d3.mouse(this);
     drawCross(coords[0], coords[1], 5, color);
    })
   }

  }
 }

</script>

<style scoped>
svg {
 height: 500px;
 width: 600px;
}
</style>