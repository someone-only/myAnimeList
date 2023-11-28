<script setup lang="ts">
definePageMeta({ auth: false })
import axios from "axios";

const popular = {
  HeaderName: "Anime populer",
  HeaderLink: "/popular",
};
const news = {
  HeaderName: "Anime Terbaru",
  HeaderLink: "/popular",
};

const topAnimeList = ref([]);

const useFetch = async () => {
  const res = await axios.get(`https://api.jikan.moe/v4/top/anime?limit=8`);
  topAnimeList.value = res.data.data;
};

onMounted(async () => {
  await useFetch();
});
</script>

<template>
  <div class="bg-dark-100 min-h-screen text-secondary-100">
    <Container>
      <template #Header>
        <AnimeListHeader v-bind="popular" />
      </template>
      <template #Content>
        <AnimeListCard :api="topAnimeList" />
      </template>
    </Container>
    <Container>
      <template #Header>
        <AnimeListHeader v-bind="news" />
      </template>
      <template #Content>
        <RandomAnimeListCard :api="recommendAnimeList" />
      </template>
    </Container>
  </div>
</template>
