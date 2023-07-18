<script setup>
import { defineProps } from 'vue'
import { Circuit } from '@/types'
const props = defineProps({
  circuit: {
    type: Circuit,
    required: true,
  },
})
</script>

<template>
  <NuxtLink :to="`/circuit/${circuit.id}`">
    <div class="border border-slate-300 p-2 rounded-sm hover:bg-slate-200">
      <div class="flex items-center space-x-4">
        <div class="flex-1 min-w-0">
          <p class="text-sm font-small text-gray-900">
            <span class="font-bold">Circuit: </span>[{{ circuit.id }}]
            {{ circuit.name }}
          </p>
          <p class="text-sm font-small text-gray-900">
            <span class="font-bold">Is main: </span
            >{{ circuit.is_main ? 'Yes' : 'No' }}
          </p>
        </div>
      </div>
    </div>
  </NuxtLink>
</template>
