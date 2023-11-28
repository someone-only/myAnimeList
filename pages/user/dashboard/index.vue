<script setup lang="ts">
const { data } = useAuth();
const user = data.value?.user;
</script>

<template>
  <div class="bg-dark-100 min-h-screen text-secondary-100">
    <h1 class="text-2xl mx-auto">Dashboard</h1>
    <div class="flex flex-col justify-center items-center">
      <img
        class="inline-block h-24 w-24 rounded-full"
        :src="user?.image"
        alt=""
      />
      <div
        class="flex flex-col bg-primary-100 shadow-sm rounded-xl p-4 md:p-5 w-[80%] mt-4"
      >
        <h3 class="text-lg font-bold text-secondary-100">
          Username: {{ user?.name }}
        </h3>
        <p class="mt-1 text-xs font-medium uppercase text-secondary-200">
          Email: {{ user?.email }}
        </p>
      </div>
    </div>
  </div>
</template>
