<template>
  <div class="flex flex-col min-h-screen">
    <header class="flex items-center border-b border-gray-600">
      <router-link to="/profile" class="p-4 mr-3 text-green-500 text-2xl">
        <i class="fas fa-user"></i>
      </router-link>

      <h1 class="text-white font-black text-xl">{{ $route.name }}</h1>
    </header>

    <main class="flex-1 overflow-scroll">
      <router-view />
    </main>

    <footer class="grid grid-cols-4 border-t border-gray-600">
      <router-link 
        v-for="(route, i) in routes"
        :key="i"
        :to="route.path" 
        :class="`p-4 text-center text-2xl ${
          (route.name == $route.name)
          ? 'text-green-500'
          : 'text-gray-300'
        }`">
        <i :class="route.iconClass"></i>
      </router-link>
    </footer>
  </div>
</template>

<script>
import { ref, onBeforeMount } from 'vue';
import { useRouter } from 'vue-router';

export default {
  setup () {
    const routes = ref([]);
    const router = useRouter();

    onBeforeMount(() => {
      routes.value = router.options.routes.filter(r => r.mainMenu);
    });

    return {
      routes
    }
  }
}
</script>
