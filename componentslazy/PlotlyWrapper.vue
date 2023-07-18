<script>
import { Plotly } from 'vue-plotly'

export default {
  components: {
    Plotly,
  },

  props: {
    dataPoints: {
      type: Array,
      required: true,
    },
    layout: {
      title: 'My graph',
    },
  },
}
</script>

<template>
  <Plotly
    :data="dataPoints"
    :layout="layout"
    :display-mode-bar="false"
  ></Plotly>
</template>
