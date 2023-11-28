<script setup lang="ts">
definePageMeta({ auth: false })
import axios from "axios";
const route = useRoute();

const search = { HeaderName: `Pencarian Untuk ${route.params.name}` };

let searchAnimeList = ref([]);

const useFetch = async () => {
  const res = await axios.get(
    `https://api.jikan.moe/v4/anime?q=${route.params.name}`
  );
  searchAnimeList.value = res.data.data;
};

watch(
  () => route.params.name,
  () => {
    useFetch();
  }
);

onMounted(async() => {
  await useFetch();
});
</script>

<template>
  <div class="bg-dark-100 min-h-screen">
    <Container>
      <template #Header>
        <AnimeListHeader v-bind="search" />
      </template>
      <template #Content>
        <AnimeListCard :api="searchAnimeList" />
      </template>
    </Container>
  </div>
</template>
