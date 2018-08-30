<template>
 <div class="skill-chart">
   <svg @click="handleClick"></svg>
 </div>
</template>

<script>
 import * as d3 from 'd3';
 export default {
  name: 'SkillChart',

  data() {
   return {
    svg: '',
    done: false,
   }
  },

  props: {
    skillColors: {
      type: Array,
      required: true,
    },
    active: {
      type: Number,
      required: true
    },
    skills: {
      type: Array,
      required: true
    }
  },

  computed: {
    color() {
      return this.skillColors[this.active];
    },
    skillStack() {
      return [...this.skills, {id: 99, name: 'DONE'}]
    },
   skill() {
    return this.skillStack[this.active];
   }
  },
  mounted() {
   this.setupD3();
  },
  methods: {
   next() {
    if(this.active !== this.skillStack.length + 1) {
     // send to parent
     this.$emit('nextSkill', this.active);
     this.done = this.active === this.skillStack.length + 1;
     return this.done;
    }
    return false;  
   },
   drawAxes() {

   },
   handleClick() {
    this.next();

   },
   setupD3() {
    const that = this;
    this.svg = d3.select('svg');
    const svg = this.svg;
    svg.append('g').attr('class', 'container');

    svg.on('click', function() {
      const color = that.color;
      const drawCross = (x, y, r) => {
       svg.select('.container')
        .append('line')
        .attr('stroke', color)
        .attr('x1', x - r)
        .attr('x2', x + r )
        .attr('y1', y - r)
        .attr('stroke-width', '3px')
        .attr('y2', y + r);

        svg.select('.container')
        .append('line')
        .attr('x1', x + r)
        .attr('x2', x - r )
        .attr('y1', y - r)
        .attr('y2', y + r)
        .attr('stroke-width', '3px')
        .attr('stroke', color);
      }
     const coords = d3.mouse(this);
     // stop adding crosses when skillstack has reached the end
     if(!that.done){
       drawCross(coords[0], coords[1], 6);
     }
    })
   }

  }
 }

</script>

<style scoped>
.skill-chart {
  display: inline-block;
}
svg {
 height: 500px;
 width: 600px;
}
</style>