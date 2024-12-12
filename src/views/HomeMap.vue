<template>
  <div id="main" class="container mx-auto" v-if="showHomePage">
    <NavBar />
    <div class="w-full flex justify-center pt-20">
      <h1 class="text-7xl text-center dragon-font">Hear the Adventure</h1>
    </div>
    <br />
    <div class="w-full flex justify-center pt-20">
      <button
        @click="navigateToSoundBoard"
        class="dragon-font bg-red-700 hover:bg-red-800 text-white font-bold py-2 px-4 rounded shadow-lg transition duration-300 ease-in-out transform hover:scale-105"
      >
        To Soundboard
      </button>
      <img src="../assets/images/DNDMAP.png" />
    </div>
  </div>
  <div v-else>
    <LoadingScreen />
  </div>
</template>

<script setup lang="ts">
import NavBar from "@/components/NavBar.vue";
import LoadingScreen from "@/components/LoadingScreen.vue";
import { ref, onMounted } from "vue";
import { useRouter } from "vue-router";

const showHomePage = ref(false);
const router = useRouter(); // Initialize router instance

const navigateToSoundBoard = () => {
  router.push({ name: "SoundBoard" }); // Navigate to the SoundBoard page
};


onMounted(() => {
  setTimeout(() => {
    showHomePage.value = true;
  }, 2000);
});
</script>

<style>
.dnd-map {
  background-image: url("../assets/images/DNDMAP.png");
}
</style>
