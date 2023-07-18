<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  async asyncData({ $axios }) {
    const circuits = await $axios.$get('http://localhost:3333/circuits')
    return { circuits }
  },
})
</script>

<template>
  <div class="flex justify-center p-3">
    <div class="flex flex-col gap-3 max-w-2xl">
      <h2 class="flex text-4xl font-bold pb-3">Circuit List</h2>
      <CircuitSmall
        v-for="circuit in circuits"
        :key="circuit.id"
        v-bind="{
          circuit,
        }"
      />
    </div>
  </div>
</template>
