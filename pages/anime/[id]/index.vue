<script setup lang="ts">
definePageMeta({ auth: false })
import axios from "axios";

const route = useRoute();
const router = useRouter();
const detailAnime = ref([]);
const isOpen = ref(false);

const useFetch = async () => {
  const res = await axios.get(
    `https://api.jikan.moe/v4/anime/${route.params.id}`
  );
  detailAnime.value = res.data.data;
};

watch(
  () => route.params.id,
  () => useFetch()
);

onBeforeUnmount(() => {
  detailAnime.value = [];
});

onMounted(() => {
  useFetch();
  scrollTo({
    behavior: "smooth",
    top: 0,
  });
});
</script>

<template>
  <div class="bg-dark-100 min-h-screen">
    <div class="py-2 px-4 text-secondary-100">
      <button @click="router.back()">Go Back</button>
    </div>
    <div class="flex flex-col py-2 text-secondary-100">
      <div v-if="detailAnime.images">
        <div
          class="aspect-h-1 aspect-w-1 px-4 w-full bg-gray-200 lg:aspect-none group-hover:opacity-75 lg:h-80 object-cover"
        >
          <img
            :src="detailAnime.images.webp.large_image_url"
            :alt="detailAnime.title"
            class="h-full w-full object-cover object-center lg:h-full lg:w-full"
          />
        </div>
      </div>
      <div class="py-2 px-4">
        <h1 class="text-2xl font-bold text-secondary-100">
          {{ detailAnime.title }}
        </h1>
      </div>
      <div
        class="px-4 pb-2 text-secondary-200 flex items-center gap-x-2 flex-wrap"
      >
        <h2 class="text-lg font-semibold">Genre:</h2>
        <div v-for="genre in detailAnime.genres" :key="genre.name">
          {{ genre.name }}
        </div>
      </div>

      <div class="px-4 text-secondary-200 flex items-center gap-x-2 flex-wrap">
        <h2 class="text-lg font-semibold">Rilis:</h2>
        <div>
          {{ detailAnime.year }}
        </div>
      </div>

      <div class="px-4 text-secondary-200">
        <h2 class="text-lg font-semibold">Synopsis:</h2>
        <p>{{ detailAnime.synopsis }}</p>
      </div>
    </div>
    <div v-if="detailAnime.trailer">
      <div v-if="isOpen && detailAnime.trailer.embed_url">
        <iframe class="w-full h-96" :src="detailAnime.trailer.embed_url">
        </iframe>
      </div>
      <div
        v-else-if="!detailAnime.trailer.embed_url"
        class="flex justify-center items-center mx-auto text-secondary-100"
      >
        <h1 class="py-2 px-4 bg-dark-200">Trailer tidak ditemukan</h1>
      </div>

      <div
        v-else-if="!isOpen"
        class="flex justify-center items-center mx-auto text-secondary-100"
      >
        <button @click="isOpen = !isOpen" class="py-2 px-4 bg-dark-200">
          Lihat Trailer
        </button>
      </div>
    </div>
  </div>
</template>
