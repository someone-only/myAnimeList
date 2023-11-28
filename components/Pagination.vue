<script setup lang="ts">
defineEmits(["updatePrevPage", "updateNextPage"]);
defineProps(["page", "lastPage"]);
</script>

<template>
  <div
    class="flex items-center justify-evenly text-secondary-100 py-4 px-2 gap-4 sm:px-6"
  >
    <div>
      <p class="text-sm text-gray-700">
        Showing
        <span class="font-medium"> {{ (page * 25 + 1) - 25 }} </span>
        <span> to </span>
        <span class="font-medium"> {{ page * 25 }} </span>
        <span> of </span>
        <span class="font-medium"> {{ lastPage }} </span>
         results
      </p>
    </div>
    <button
      class="relative inline-flex items-center rounded-md border border-gray-300 bg-white px-4 py-2 text-sm font-medium text-gray-700 hover:bg-gray-50"
      v-if="page > 1"
      @click="$emit('updatePrevPage')"
    >
      Previous
    </button>
    <button
      class="relative ml-3 inline-flex items-center rounded-md border border-gray-300 bg-white px-4 py-2 text-sm font-medium text-gray-700 hover:bg-gray-50"
      @click="$emit('updateNextPage')"
    >
      Next
    </button>
  </div>
</template>
