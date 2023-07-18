<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  async asyncData({ $axios, params }) {
    const { id } = params
    const { circuit, payload } = await $axios.$get(
      'http://localhost:3333/circuits/' + id
    )
    return { circuit, dataPoints: [payload] }
  },
})
</script>

<template>
  <div class="flex flex-col gap-3 w-full justify-center">
    <div class="flex text-xl justify-center">
      <span class="font-bold">Circuit:&nbsp;</span> {{ circuit.name }}
    </div>
  </div>
</template>
