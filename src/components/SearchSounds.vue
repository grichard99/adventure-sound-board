<template>
  <div class="flex flex-col items-center pt-10 pb-8 shadow-md rounded-xl">
    <h2
      class="text-3xl font-light text-gray-900 dark:text-gray-100 mb-6 mt-10 sm:mt-6 text-center sm:text-left"
    >
      Find Your Sounds
    </h2>
    <div class="relative w-full sm:w-3/4 mb-6">
      <div class="flex justify-center w-full">
        <input
          type="text"
          v-model="searchQuery"
          placeholder="Search sounds..."
          class="flex-grow p-3 pl-10 border border-gray-300 rounded-l-2xl text-black focus:outline-none focus:ring-2 focus:ring-red-700 transition"
          @input="(event: Event) => filterSounds(event)"
        />
        <button
          @click="showFilters = !showFilters"
          class="bg-red-700 text-white px-4 py-2 rounded-r-2xl shadow-md hover:bg-red-800 transition duration-300"
        >
          Filters
        </button>
        <svg
          class="absolute left-2 sm:left-4 top-1/2 transform -translate-y-1/2 text-gray-500"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          width="20"
          height="20"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M21 21l-4.35-4.35M16.5 10.5a6 6 0 11-12 0 6 6 0 0112 0z"
          />
        </svg>
      </div>
      <div class="relative">
        <div
          v-if="showFilters"
          class="mt-2 bg-white dark:bg-gray-800 border border-gray-300 rounded-xl shadow-lg p-4 space-y-4 w-full sm:w-1/3 sm:ml-auto"
        >
          <div class="flex items-center" @click="toggleActiveFilter">
            <label
              for="active-sounds"
              class="flex items-center ml-2 text-gray-900 dark:text-gray-100 cursor-pointer"
            >
              <input
                type="checkbox"
                id="active-sounds"
                class="accent-red-600 form-checkbox h-5 w-5 text-red-600 bg-red-600 checked:bg-red-600 focus:ring-red-600 transition duration-150 ease-in-out"
                :checked="showActiveOnly"
              />
              <span class="ml-2">Active Sounds</span>
            </label>
          </div>
          <div class="flex items-center" @click="toggleFavoriteFilter">
            <label
              for="favorite-sounds"
              class="flex items-center ml-2 text-gray-900 dark:text-gray-100 cursor-pointer"
            >
              <input
                type="checkbox"
                id="favorite-sounds"
                class="accent-red-600 form-checkbox h-5 w-5 text-red-600 transition duration-150 ease-in-out"
                :checked="showFavoritesOnly"
              />
              <span class="ml-2">Favorite Sounds</span>
            </label>
          </div>
          <div class="flex items-center">
            <label
              for="all-sounds"
              class="flex items-center ml-2 text-gray-900 dark:text-gray-100 cursor-pointer"
            >
              <span class="ml-2">More Filters Coming Soon</span>
            </label>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
//define props
defineProps<{
  showActiveOnly: boolean;
  showFavoritesOnly: boolean;
}>();

// Define an emit function to emit the "filter-sounds" event with the updated searchQuery value
const emit = defineEmits<{
  (e: "filter-sounds", value: string): void;
  (e: "toggle-active-filter"): void;
  (e: "toggle-favorite-filter"): void;
}>();

const searchQuery = ref("");
const showFilters = ref(false);

const filterSounds = (event: Event) => {
  // Update the searchQuery value with the input value
  searchQuery.value = (event.target as HTMLInputElement).value;

  // Emit the "filter-sounds" event with the updated searchQuery value
  emit("filter-sounds", searchQuery.value);
};

const toggleActiveFilter = () => {
  console.log("toggleActiveFilter");
  emit("toggle-active-filter");
};

const toggleFavoriteFilter = () => {
  console.log("toggleFavoriteFilter");
  emit("toggle-favorite-filter");
};
</script>
