<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  async asyncData({ $axios, params }) {
    try {
      const { id } = params
      const { circuit, payload } = await $axios.$get(
        'http://localhost:3333/circuits/' + id
      )

      payload.data.type = 'scatter'
      return { circuit, dataPoints: [payload?.data] }
    } catch (e: any) {
      return { error: e }
    }
  },
  components: {
    PlotlyWrapper: () => import('./../../componentslazy/PlotlyWrapper.vue'),
  },
})
</script>

<template>
  <div class="flex flex-col gap-3 w-full justify-center">
    <div v-if="dataPoints">
      <div class="flex text-xl justify-center">
        <span class="font-bold">Circuit:&nbsp;</span> {{ circuit.name }}
      </div>
      <client-only>
        <PlotlyWrapper
          class="min-h-[500px] max-h-[calc(100vh-150px)]"
          v-bind="{ dataPoints }"
        />
      </client-only>
    </div>
    <div class="flex text-xl justify-center" v-if="error">
      <p class="text-red-500 text-2xl">
        Error generating graph
        {{ error?.message ? ` - ${error?.message}` : '' }}
      </p>
    </div>
  </div>
</template>
