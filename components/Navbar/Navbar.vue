<script setup lang="ts">
import InputSearch from "./InputSearch.vue";
import UserActionButton from "./UserActionButton.vue"; 
</script>

<template>
  <nav class="bg-dark-100 border-b-dark-300 border-2">
    <div class="mx-auto w-full px-2 sm:px-6 lg:px-8 py-2">
      <div class="flex flex-col md:flex-row md:items-center md:justify-between gap-y-2">
        <NuxtLink class="text-secondary-100" to="/">
          <h1 class="text-2xl font-bold">AnimeList</h1>
        </NuxtLink>
        <InputSearch />
        <UserActionButton />
      </div>
    </div>
  </nav>
</template>
