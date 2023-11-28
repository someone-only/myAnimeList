<script setup lang="ts">
const { data } = useAuth();
const user = data.value;
</script>

<template>
  <div class="flex justify-center items-center gap-x-2">
    <div>
      <NuxtLink
        to="user/dashboard"
        v-if="user"
        class="text-secondary-100 py-1 px-2"
        >Dashboard</NuxtLink
      >
      <div v-else></div>
    </div>
    <div>
      <NuxtLink
        v-if="!user"
        to="/api/auth/signin"
        class="py-1 px-16 text-secondary-100 bg-primary-100 rounded-md"
      >
        Sign In
      </NuxtLink>
      <NuxtLink
        v-else-if="user"
        to="/api/auth/signout"
        class="py-1 px-16 text-secondary-100 bg-primary-100 rounded-md"
      >
        Sign Out
      </NuxtLink>
    </div>
  </div>
</template>
