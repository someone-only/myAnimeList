<script setup lang="ts">
defineProps(["api"]);
</script>

<template>
    <div
      class="mt-6 grid grid-cols-2 gap-x-6 gap-y-10 sm:grid-cols-4 lg:grid-cols-8 xl:gap-x-8"
    >
      <NuxtLink
        class="group relative bg-primary-100 rounded-lg overflow-hidden"
        :to="`/anime/${anime.mal_id}`"
        v-for="anime in api"
        :key="anime.mal_id"
      >
        <div
          class="aspect-h-1 aspect-w-1 w-full bg-gray-200 lg:aspect-none group-hover:opacity-75 lg:h-80 object-cover"
        >
          <img
            :src="anime.images.webp.large_image_url"
            :alt="anime.title"
            class="h-full w-full object-cover object-center lg:h-full lg:w-full"
          />
        </div>
        <div class="mt-4 px-4 flex justify-between">
          <div>
            <h3 class="text-sm text-primary-300">
              <a href="#">
                <span aria-hidden="true" class="absolute inset-0"></span>
                {{ anime.title }}
              </a>
            </h3>
            <div class="flex gap-x-4 pb-4 flex-wrap">
              <p
                class="mt-1 text-sm text-primary-200"
                v-for="genre in anime.genres"
              >
                {{ genre.name }}
              </p>
            </div>
          </div>
          <p class="text-sm font-medium text-primary-300">
            {{ anime.score }}
          </p>
        </div>
      </NuxtLink>
    </div>
</template>
