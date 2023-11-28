<script setup lang="ts">
definePageMeta({ auth: false })
import axios from "axios";

const router = useRouter();
const route = useRoute()
const topAnimeList = ref();
const page = ref(1)
const lastPage = ref();
const currentPage = ref();
const popular = {
  HeaderName: currentPage,
};

const scrollTop = () => {
  scrollTo({
    behavior: "smooth",
    top: 0,
  });
};

const updateNextPage = () => {
  page.value += 1;
  scrollTop();
};
const updatePrevPage = () => {
  if (page.value > 1) {
    page.value -= 1;
    scrollTop();
  }
};

const useFetch = async () => {
  const res = await axios.get(
    `https://api.jikan.moe/v4/top/anime?page=${page.value}`
  );
  topAnimeList.value = res.data.data;
  lastPage.value = res.data.pagination.last_visible_page;
  currentPage.value = res.data.pagination.current_page;
};

watch(
  () => page.value,
  () => {
    useFetch();
  }
);

onMounted(async () => {
  await useFetch();
});
</script>

<template>
  <div class="bg-dark-100 min-h-screen">
    <Container>
      <template #Header>
        <Header v-bind="popular" />
      </template>
      <template #Content>
        <AnimeListCard :api="topAnimeList" />
        <Pagination
          :page="page"
          :last-page="lastPage"
          @update-prev-page="updatePrevPage"
          @update-next-page="updateNextPage"
        />
      </template>
    </Container>
  </div>
</template>
