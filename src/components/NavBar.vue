<!-- eslint-disable prettier/prettier -->
<script setup>
  import { ref } from 'vue'
  import { useAuth } from '@/composables/useAuth'

  const { isAuthenticated, logout, user } = useAuth()

  const brand = ref(import.meta.env.VITE_APP_EMM)
</script>

<template>
  <nav>
    <div class="wrapper">
      <RouterLink :to="{ name: 'Home' }" class="brand">
        <span class="brand-title">{{ brand }}</span>
      </RouterLink>
      <div class="menu">
        <div v-if="isAuthenticated">
          <i v-show="isAuthenticated" class="px-2 py-4"
            >Welcome back <strong>{{ user.name }}</strong></i
          >
          <RouterLink :to="{ name: 'Settings' }" href="#" class="menu-item">Settings</RouterLink>

          <button class="menu-logout" @click="logout">Logout</button>
        </div>

        <div v-else>
          <RouterLink :to="{ name: 'Login' }" href="#" class="menu-login">Login</RouterLink>
        </div>
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
        div {
          @apply py-2;
        }
        &-item {
          @apply rounded-md px-4 py-2 font-semibold hover:bg-yellow-300 hover:text-blue-400;
        }
        &-login {
          @apply mx-2 rounded-md bg-green-400 px-4 py-2 font-bold text-yellow-300 hover:bg-green-300 hover:text-blue-400;
        }
        &-logout {
          @apply mx-2 rounded-md bg-red-400 px-4 py-2 font-bold hover:bg-red-300 hover:text-blue-400;
        }
      }
    }
  }
</style>
