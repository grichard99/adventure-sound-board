<template>
  <header
    class="fixed top-0 left-0 w-full z-50 transition-colors duration-300 py-4"
    :class="scrolled ? 'bg-red-900' : 'bg-red-700'"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-center items-center h-full">
        <h1 class="flex text-5xl dragon-font text-center">
          Adventure Sound Board
        </h1>
      </div>
    </div>
  </header>
</template>

<script lang="ts">
import { ref, onMounted, onUnmounted } from "vue";

export default {
  setup() {
    const scrolled = ref(false);
    const menuOpen = ref(false);

    const handleScroll = () => {
      scrolled.value = window.scrollY > 50;
    };

    const toggleMenu = () => {
      menuOpen.value = !menuOpen.value;
    };

    onMounted(() => {
      window.addEventListener("scroll", handleScroll);
    });

    onUnmounted(() => {
      window.removeEventListener("scroll", handleScroll);
    });

    return {
      scrolled,
      menuOpen,
      toggleMenu,
    };
  },
};
</script>
