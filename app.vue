<script setup>
import { ref, onMounted } from "vue";

const targetDate = new Date(Date.UTC(2024, 5, 9, 9)); // Sätt ditt måldatum här

const days = ref(0);
const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);

onMounted(() => {
  setInterval(() => {
    const now = new Date();
    const diff = Math.max((targetDate - now) / 1000, 0);

    days.value = Math.floor(diff / 86400);
    hours.value = Math.floor(diff / 3600) % 24;
    minutes.value = Math.floor(diff / 60) % 60;
    seconds.value = Math.floor(diff) % 60;
  }, 1000);
});
</script>

<template>
  <div
    class="custom-container text-white flex flex-col items-center justify-center h-screen w-full bg-center bg-no-repeat bg-cover"
    style="background-image: url(img/sardini.jpg)"
  >
    <h1
      class="text-4xl sm:text-5xl md:text-6xl uppercase mb-5 text-center px-4 custom-effect"
    >
      Familjen Friman
    </h1>
    <h2
      class="text-3xl sm:text-4xl md:text-5xl uppercase mb-5 text-center px-4"
    >
      going to sardinien in
    </h2>
    <div
      class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-5 text-center mt-5"
    >
      <div class="flex flex-col bg-amber-300 rounded text-zinc-900 p-3">
        <span class="countdown font-mono text-4xl sm:text-6xl md:text-8xl">
          <span :style="`--value: ${days}`"></span>
        </span>
        days
      </div>
      <div class="flex flex-col bg-amber-300 rounded text-zinc-900 p-3">
        <span class="countdown font-mono text-4xl sm:text-6xl md:text-8xl">
          <span :style="`--value: ${hours}`"></span>
        </span>
        hours
      </div>
      <div class="flex flex-col bg-amber-300 rounded text-zinc-900 p-3">
        <span class="countdown font-mono text-4xl sm:text-6xl md:text-8xl">
          <span :style="`--value: ${minutes}`"></span>
        </span>
        min
      </div>
      <div class="flex flex-col bg-amber-300 rounded text-zinc-900 p-3">
        <span class="countdown font-mono text-4xl sm:text-6xl md:text-8xl">
          <span :style="`--value: ${seconds}`"></span>
        </span>
        sec
      </div>
    </div>
  </div>
</template>

<style>
.custom-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100vh;
  width: 100%;
  background-image: url(img/sardini.jpg);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;

  .custom-effect {
    animation: fadeIn 2s ease-in-out;
    text-shadow: rgb(212, 212, 212) 0px 0px 56px;
    text-shadow: rgba(62, 66, 66, 0.4) 0px 10px 24px;

    -webkit-box-shadow: 0px 0px 105px 45px rgba(45, 255, 196, 0.9);
    -moz-box-shadow: 0px 0px 105px 45px rgba(45, 255, 196, 0.9);
    box-shadow: 0px 0px 105px 45px rgba(45, 255, 196, 0.9);
  }
}
</style>
