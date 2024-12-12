<template>
  <div class="sound-container">
    <div class="sound-name text-center mb-4 font-bold text-black">
      {{ sound.name }}
    </div>
    <div class="flex justify-between items-center">
      <button
        @click="toggleFavorite(sound)"
        :class="[
          'favorite-button text-2xl transition-colors duration-300',
          sound.isFavorite ? 'text-red-500' : 'text-gray-400',
        ]"
      >
        ♥
      </button>
      <button
        :class="[
          'play-button flex justify-center items-center rounded-full shadow-lg transition duration-300 ease-in-out w-20 h-20',
          sound.isPlaying ? 'bg-green-600' : 'bg-red-700 hover:bg-red-800',
        ]"
        @click="togglePlay(sound)"
      >
        <span class="text-lg">{{ sound.isPlaying ? "Pause" : "Play" }}</span>
      </button>
    </div>
    <div class="controls mt-4 flex flex-col items-center">
      <input
        type="range"
        class="volume-slider"
        min="0"
        max="1"
        step="0.01"
        v-model="sound.volume"
        @input="changeVolume(sound)"
        aria-label="Volume control"
      />
      <span class="volume-label text-sm text-gray-500 mt-2"
        >{{ (sound.volume * 100).toFixed(0) }}%</span
      >
      <div class="button-group mt-2 flex justify-around w-full">
        <button
          @click="toggleLoop(sound)"
          :class="[
            'loop-button text-sm rounded-full px-4 py-2 transition-colors duration-300',
            sound.isLooping
              ? 'bg-blue-600 text-white'
              : 'bg-gray-300 text-black',
          ]"
        >
          &#x21BB;
        </button>
        <button
          @click="restartSound(sound)"
          class="restart-button bg-gray-300 text-black rounded-full px-4 py-2"
        >
          &#x21A9;
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  sound: {
    name: string;
    isPlaying: boolean;
    isFavorite: boolean;
    isLooping: boolean;
    volume: number;
    audio: HTMLAudioElement;
    listenerAdded: boolean;
    progress: number;
  };
}>();
const toggleFavorite = (sound: any) => {
  sound.isFavorite = !sound.isFavorite;
};

const togglePlay = (sound: any) => {
  if (sound.isPlaying) {
    sound.audio.pause();
    sound.isPlaying = false;
  } else {
    sound.audio.loop = sound.isLooping;
    sound.audio.play();
    sound.isPlaying = true;

    if (!sound.listenerAdded) {
      sound.audio.addEventListener("ended", () => {
        if (!sound.isLooping) sound.isPlaying = false;
      });
      sound.listenerAdded = true;
    }

    const updateProgress = () => {
      if (!sound.isPlaying) return;
      sound.progress = (sound.audio.currentTime / sound.audio.duration) * 100;
      requestAnimationFrame(updateProgress);
    };
    updateProgress();
  }
};

const toggleLoop = (sound: any) => {
  sound.isLooping = !sound.isLooping;
  sound.audio.loop = sound.isLooping;
};

const changeVolume = (sound: any) => {
  sound.audio.volume = sound.volume;
};

const restartSound = (sound: any) => {
  sound.audio.currentTime = 0;
  if (!sound.isPlaying) {
    sound.audio.pause();
  }
};
</script>

<style>
.sound-container {
  width: 100%;
  max-width: 300px;
  margin: 0 auto 16px;
  padding: 16px;
  border: 1px solid rgba(60, 60, 67, 0.29);
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.12);
  background-color: #ffffff;
}

.play-button {
  width: 80px;
  height: 80px;
  font-size: 16px;
  color: #ffffff;
  transition: all 0.3s ease-in-out;
  border-radius: 50%;
  background-color: #ff3b30;
}

.volume-slider {
  -webkit-appearance: none;
  appearance: none;
  width: 80%;
  height: 10px;
  background: linear-gradient(to right, #ff3b30, #e0e0e0);
  border-radius: 5px;
  outline: none;
  cursor: pointer;
}

.volume-slider::-webkit-slider-thumb {
  width: 20px;
  height: 20px;
  background: #ffffff;
  border: 2px solid #ff3b30;
  border-radius: 50%;
  cursor: pointer;
}

.button-group {
  display: flex;
  justify-content: space-between;
  gap: 10px;
}

.loop-button,
.restart-button {
  width: 50px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 8px;
  background-color: #f2f2f7;
  color: #ff3b30;
}

.favorite-button {
  cursor: pointer;
  font-size: 24px;
  transition: color 0.3s ease;
  color: #d3d3d3; /* Default to off-gray */
}

.favorite-button.text-red-500 {
  color: #ff3b30; /* Turn red when active */
}

.favorite-button.active {
  color: #ff3b30; /* Turn red once clicked */
}
</style>
