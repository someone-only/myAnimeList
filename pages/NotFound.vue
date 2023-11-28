<script setup lang="ts">
import { RouterLink } from "vue-router";
</script>

<template>
  <div
    class="bg-dark-100 min-h-screen flex flex-col justify-center items-center text-secondary-100"
  >
    <h1 class="font-black text-3xl">404 | PAGE NOT FOUND</h1>
    <RouterLink to="/" class="mt-2">Kembali</RouterLink>
  </div>
</template>
