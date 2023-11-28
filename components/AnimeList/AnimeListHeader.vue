<script setup lang="ts">

const { HeaderName, HeaderLink } = defineProps(["HeaderName", "HeaderLink"]);
</script>

<template>
  <div class="flex justify-between items-center text-secondary-100">
    <h2 class="text-2xl font-bold tracking-tight">
      {{ HeaderName }}
    </h2>
    <div v-if="HeaderLink">
      <NuxtLink :to="HeaderLink">Lihat Selengkapnya </NuxtLink>
    </div>
    <div v-else></div>
  </div>
</template>
