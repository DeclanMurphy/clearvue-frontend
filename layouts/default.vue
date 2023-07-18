<script setup lang="ts"></script>

<template>
  <div class="min-h-screen flex flex-col">
    <header class="bg-slate-200 p-2">
      <div class="flex justify-center items-center">
        <p class="text-slate-500 uppercase">Header</p>
      </div>
    </header>
    <div class="flex-1 flex flex-col sm:flex-row">
      <nav class="order-first sm:w-40 bg-slate-300 flex flex-col gap-2 p-5">
        <NuxtLink class="text-slate-500 hover:text-slate-700" to="/"
          >All circuits</NuxtLink
        >
      </nav>
      <main class="flex-1 bg-white p-3">
        <Nuxt />
      </main>
    </div>
    <footer class="bg-slate-200 flex justify-center p-2">
      <div class="text-slate-500 uppercase">Footer</div>
    </footer>
  </div>
</template>
