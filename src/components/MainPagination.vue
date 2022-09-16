<script setup>
  import { ref } from 'vue'
  const pages = ref(10)
  const activePage = ref(4)

  const prevPage = () => {
    if (activePage.value > 1) {
      activePage.value--
    }
  }

  const nextPage = () => {
    if (activePage.value < pages.value) {
      activePage.value++
    }
  }
</script>

<template>
  <div class="pagination">
    <button class="action" :disabled="activePage === 1" @click="prevPage">Prev</button>

    <button v-for="page in pages" class="page" :class="page === activePage ? 'active' : ''" @click="activePage = page">
      {{ page }}
    </button>
    <button class="action" :disabled="activePage === pages" @click="nextPage">Next</button>
  </div>
</template>

<style lang="postcss" scoped>
  .pagination {
    @apply flex justify-center gap-4;

    .action {
      @apply rounded-md bg-slate-100 p-2 font-medium text-blue-400 shadow-md hover:bg-slate-200 disabled:text-blue-400 hover:disabled:bg-slate-100;
    }
    .page {
      @apply rounded-md bg-slate-100 pt-2 font-medium text-blue-400 shadow-md hover:bg-slate-200;
      &.active {
        @apply bg-blue-400 text-white;
      }
    }
  }
</style>
