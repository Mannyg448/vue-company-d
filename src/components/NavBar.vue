<!-- eslint-disable prettier/prettier -->
<script setup>
  import { ref } from 'vue'
  const brand = ref('🏢 Fake Company Directory')
</script>

<template>
  <nav>
    <div class="wrapper">
      <div class="brand">
        <span class="brand-title">{{ brand }}</span>
      </div>
      <div class="menu">
        <a href="#" class="menu-item">Departments</a>
        <a href="#" class="menu-item">Settings</a>
        <a href="#" class="menu-login">Logout</a>
      </div>
    </div>
  </nav>
</template>

<style scoped lang="postcss">
  nav {
    @apply flex h-20 items-center justify-between bg-blue-400 text-yellow-300;

    .wrapper {
      @apply container mx-auto flex items-center justify-between;

      .brand {
        &-title {
          @apply text-2xl font-extrabold text-white;
        }
      }
      .menu {
        @apply flex gap-2;
        &-item {
          @apply rounded-md px-4 py-2 font-semibold hover:bg-yellow-300 hover:text-blue-400;
        }
        &-login {
          @apply rounded-md bg-red-400 px-4 py-2 font-bold hover:bg-green-300 hover:text-blue-400;
        }
      }
    }
  }
</style>
