<script setup lang="ts">
const { HeaderName } = defineProps(["HeaderName"]);
</script>

<template>
  <div class="flex justify-center items-center mx-auto text-secondary-100">
    <h2 class="text-2xl font-bold tracking-tight">
      Page #{{ HeaderName }}
    </h2>
  </div>
</template>
