<template>
  <div id="soundboard" class="container mx-auto px-4">
    <NavBar />

    <!-- Search and Filter Section -->
    <SearchSounds
      :show-active-only="showActiveOnly"
      :show-favorites-only="showFavoritesOnly"
      @filter-sounds="filterSounds"
      @toggle-active-filter="toggleActiveFilter"
      @toggle-favorite-filter="toggleFavoriteFilter"
    />
    <!-- Active Sounds Section -->
    <div v-if="showActiveOnly" class="pt-10">
      <h2 class="text-4xl text-center dragon-font">Active Sounds</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 pt-10">
        <div v-for="(sound, index) in filteredSounds" :key="index">
          <SoundCard :sound="sound" />
        </div>
      </div>
    </div>

    <!-- Music Section -->
    <div v-if="!showActiveOnly && filteredMusicSounds.length" class="pt-10">
      <h2 class="text-4xl text-center dragon-font">Music</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 pt-10">
        <div v-for="(sound, index) in filteredMusicSounds" :key="index">
          <SoundCard :sound="sound" />
        </div>
      </div>
    </div>

    <div v-else-if="!showActiveOnly" class="text-center text-gray-500">
      No music sounds available.
    </div>

    <!-- Environment Section -->
    <div
      v-if="!showActiveOnly && filteredEnvironmentSounds.length"
      class="pt-10"
    >
      <h2 class="text-4xl text-center dragon-font">Environment</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 pt-10">
        <div v-for="(sound, index) in filteredEnvironmentSounds" :key="index">
          <SoundCard :sound="sound" />
        </div>
      </div>
    </div>

    <div v-else-if="!showActiveOnly" class="text-center text-gray-500">
      No environment sounds available.
    </div>

    <!-- Activity Section -->
    <div v-if="!showActiveOnly && filteredActivitySounds.length" class="pt-10">
      <h2 class="text-4xl text-center dragon-font">Activity</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 pt-10">
        <div v-for="(sound, index) in filteredActivitySounds" :key="index">
          <SoundCard :sound="sound" />
        </div>
      </div>
    </div>

    <div v-else-if="!showActiveOnly" class="text-center text-gray-500">
      No activity sounds available.
    </div>
  </div>
</template>

<script setup lang="ts">
import NavBar from "@/components/NavBar.vue";
import SearchSounds from "@/components/SearchSounds.vue";
import SoundCard from "@/components/SoundCard.vue";
import { ref, computed } from "vue";

const createSound = (name: string, file: string) => {
  const audio = new Audio(file);
  return {
    name,
    file,
    audio,
    isPlaying: false,
    isLooping: false,
    isFavorite: false,
    volume: 1,
    progress: 0,
    listenerAdded: false,
  };
};

const searchQuery = ref("");
const showActiveOnly = ref(false);
const showFavoritesOnly = ref(false);

const filterSounds = (value: string) => {
  searchQuery.value = value;
};

const musicSounds = ref([
  createSound(
    "Fantasy Kingdom",
    new URL("@/assets/audio/fantasy-kingdom-261257.mp3", import.meta.url).href
  ),
  createSound(
    "Epic Adventure",
    new URL(
      "@/assets/audio/epic-steampunk-action-adventure-fantasy-music-194750.mp3",
      import.meta.url
    ).href
  ),
  createSound(
    "Ethereal Music",
    new URL("@/assets/audio/ethereal-music.mp3", import.meta.url).href
  ),
  createSound(
    "Upbeat Irish Fiddle",
    new URL("@/assets/audio/upbeat-irish-fiddle.mp3", import.meta.url).href
  ),
  createSound(
    "Dancing Fiddle",
    new URL("@/assets/audio/dancing-fiddle.mp3", import.meta.url).href
  ),
  createSound(
    "Irish Harp",
    new URL("@/assets/audio/Irish-Harp.mp3", import.meta.url).href
  ),
  createSound(
    "Light Lute",
    new URL("@/assets/audio/light-lute.mp3", import.meta.url).href
  ),
]);

const environmentSounds = ref([
  createSound(
    "Upbeat Tavern",
    new URL("@/assets/audio/upbeat-tavern.mp3", import.meta.url).href
  ),
  createSound(
    "Tavern with Fire",
    new URL("@/assets/audio/tavern-ambience-with-fire.mp3", import.meta.url)
      .href
  ),
  createSound(
    "Mellow Tavern",
    new URL("@/assets/audio/ambient-pub-6696.mp3", import.meta.url).href
  ),
  createSound(
    "Campfire",
    new URL("@/assets/audio/campfire.mp3", import.meta.url).href
  ),
  createSound(
    "Fire Crackle",
    new URL("@/assets/audio/campfire-crackling.mp3", import.meta.url).href
  ),
  createSound(
    "Forest",
    new URL("@/assets/audio/forest-163012.mp3", import.meta.url).href
  ),
  createSound(
    "Birds in Forest",
    new URL(
      "@/assets/audio/bird-whistling-in-the-forest-215441.mp3",
      import.meta.url
    ).href
  ),
  createSound(
    "Bubbling Lava",
    new URL("@/assets/audio/lava-bubbling.mp3", import.meta.url).href
  ),
  createSound(
    "Swamp Woods",
    new URL("@/assets/audio/swampy-woods.mp3", import.meta.url).href
  ),
  createSound(
    "Swamp Daytime",
    new URL("@/assets/audio/daytime-swamp.mp3", import.meta.url).href
  ),
  createSound(
    "Low Growl",
    new URL("@/assets/audio/low-growl.mp3", import.meta.url).href
  ),
  createSound(
    "Dragon Growl",
    new URL("@/assets/audio/dragon-growl.mp3", import.meta.url).href
  ),
  createSound(
    "Wolf Growl",
    new URL("@/assets/audio/wolf-growling.mp3", import.meta.url).href
  ),
  createSound(
    "Lone Howl",
    new URL("@/assets/audio/lone-wolf-howl.mp3", import.meta.url).href
  ),
  createSound(
    "Distant Dragon",
    new URL("@/assets/audio/distant-intermittent-dragon.mp3", import.meta.url)
      .href
  ),
  createSound(
    "Dragon Roar",
    new URL("@/assets/audio/dragon-roar.mp3", import.meta.url).href
  ),
  createSound(
    "Sleeping Dragon",
    new URL("@/assets/audio/dragon-sleeping.mp3", import.meta.url).href
  ),
  createSound(
    "Giant Wings",
    new URL("@/assets/audio/giant-wings-flapping.mp3", import.meta.url).href
  ),
  createSound(
    "Flapping Wings",
    new URL("@/assets/audio/flapping-wings-close.mp3", import.meta.url).href
  ),
  createSound(
    "Ocean Waves",
    new URL("@/assets/audio/ocean-waves.mp3", import.meta.url).href
  ),
  createSound(
    "Whistling Wind",
    new URL("@/assets/audio/wind-whistling.mp3", import.meta.url).href
  ),
  createSound(
    "Creaking Wood",
    new URL("@/assets/audio/wood-creaking.mp3", import.meta.url).href
  ),
  createSound(
    "Cave Drips",
    new URL("@/assets/audio/cave-waterdrops.mp3", import.meta.url).href
  ),
  createSound(
    "Religious Chanting",
    new URL("@/assets/audio/religious-chant.mp3", import.meta.url).href
  ),
  createSound(
    "Tibetan Monks",
    new URL("@/assets/audio/tibetan-monks.mp3", import.meta.url).href
  ),
  createSound(
    "Howling Wind",
    new URL("@/assets/audio/howling-wind.mp3", import.meta.url).href
  ),
  createSound(
    "Loud Thunder",
    new URL("@/assets/audio/loud-thunder.mp3", import.meta.url).href
  ),
  createSound(
    "Distant Rolling Thunder",
    new URL(
      "@/assets/audio/distant-thunder-rolling-noRain.mp3",
      import.meta.url
    ).href
  ),
]);

const activitySounds = ref([
  createSound(
    "Door Unlock",
    new URL("@/assets/audio/key-door-unlock.mp3", import.meta.url).href
  ),
  createSound(
    "Walking Chains",
    new URL("@/assets/audio/chains-walking.mp3", import.meta.url).href
  ),
  createSound(
    "Cork Pop",
    new URL("@/assets/audio/cork-pop.mp3", import.meta.url).href
  ),
  createSound(
    "Paper Writing",
    new URL("@/assets/audio/writing-on-paper.mp3", import.meta.url).href
  ),
  createSound(
    "Glass Smash",
    new URL("@/assets/audio/glass-smash.mp3", import.meta.url).href
  ),
  createSound(
    "Coin Drop",
    new URL("@/assets/audio/coin-drop.mp3", import.meta.url).href
  ),
  createSound(
    "Coins Dropping",
    new URL("@/assets/audio/several-coins-dropping.mp3", import.meta.url).href
  ),
  createSound(
    "Spell Cast",
    new URL("@/assets/audio/spell-swoosh.mp3", import.meta.url).href
  ),
  createSound(
    "Arrow Hit",
    new URL("@/assets/audio/arrow-impact.mp3", import.meta.url).href
  ),
  createSound(
    "Marching Army",
    new URL("@/assets/audio/army-marching.mp3", import.meta.url).href
  ),
  createSound(
    "Hooves",
    new URL("@/assets/audio/horses-hooves.mp3", import.meta.url).href
  ),
  createSound(
    "Distant Sword Fighting",
    new URL("@/assets/audio/sword-hits-distant.mp3", import.meta.url).href
  ),
  createSound(
    "Sword Fighting",
    new URL("@/assets/audio/sword-and-shield-fighting.mp3", import.meta.url)
      .href
  ),
]);

const filteredSounds = computed(() => {
  const allSounds = [
    ...musicSounds.value,
    ...environmentSounds.value,
    ...activitySounds.value,
  ];
  return allSounds.filter((sound) => {
    return (
      (!showActiveOnly.value || sound.isPlaying) &&
      (!showFavoritesOnly.value || sound.isFavorite) &&
      sound.name.toLowerCase().includes(searchQuery.value.toLowerCase())
    );
  });
});

const filteredMusicSounds = computed(() => {
  return musicSounds.value.filter((sound) => {
    return (
      (!showActiveOnly.value || sound.isPlaying) &&
      (!showFavoritesOnly.value || sound.isFavorite) &&
      sound.name.toLowerCase().includes(searchQuery.value.toLowerCase())
    );
  });
});

const filteredEnvironmentSounds = computed(() => {
  return environmentSounds.value.filter((sound) => {
    return (
      (!showActiveOnly.value || sound.isPlaying) &&
      (!showFavoritesOnly.value || sound.isFavorite) &&
      sound.name.toLowerCase().includes(searchQuery.value.toLowerCase())
    );
  });
});

const filteredActivitySounds = computed(() => {
  return activitySounds.value.filter((sound) => {
    return (
      (!showActiveOnly.value || sound.isPlaying) &&
      (!showFavoritesOnly.value || sound.isFavorite) &&
      sound.name.toLowerCase().includes(searchQuery.value.toLowerCase())
    );
  });
});

const toggleActiveFilter = () => {
  showActiveOnly.value = !showActiveOnly.value;
};

const toggleFavoriteFilter = () => {
  showFavoritesOnly.value = !showFavoritesOnly.value;
};
</script>

<style></style>
