<script setup>
import Button from "./components/Button.vue";
import LastButton from "./components/LastButton.vue";
import "./style.css";
import { ref } from "vue";

const buttons = [
  {
    name: "Hungry",
    icon: "icons/hungry.png",
    audio: "audio/hungry.mp3",
    class: "bg-orange-500",
  },
  {
    name: "Thirsty",
    icon: "icons/thirsty.png",
    audio: "audio/thirsty.mp3",
    class: "bg-orange-500",
  },
  {
    name: "Sleepy",
    icon: "icons/sleepy.png",
    audio: "audio/sleepy.mp3",
    class: "bg-cyan-500",
  },
  {
    name: "Tired",
    icon: "icons/tired.png",
    audio: "audio/tired.mp3",
    class: "bg-orange-500",
  },
  {
    name: "Outside",
    icon: "icons/outside.png",
    audio: "audio/outside.mp3",
    class: "bg-gray-100",
  },
  {
    name: "Hot",
    icon: "icons/hot.png",
    audio: "audio/hot.mp3",
    class: "bg-yellow-400",
  },
  {
    name: "Hurt",
    icon: "icons/hurt.png",
    audio: "audio/hurt.mp3",
    class: "bg-red-500",
  },
  {
    name: "Poop",
    icon: "icons/poop.png",
    audio: "audio/poop.mp3",
    class: "bg-sky-500",
  },
  {
    name: "Pee",
    icon: "icons/pee.png",
    audio: "audio/pee.mp3",
    class: "bg-sky-500",
  },
];

const lastButton = ref(null);

const getButton = (name) => {
  return buttons.find((button) => button.name === name);
};

const pressButton = (button) => {
  // Set the LastButton
  lastButton.value = button;

  // Play the audio
  const audio = new Audio(getButton(button).audio);
  audio.play();

  setTimeout(() => {
    lastButton.value = null;
  }, 2 * 60 * 1000);
};
</script>

<template>
  <div class="absolute h-full w-full bg-sky-500 opacity-20 z-10"></div>
  <div class="h-screen w-screen justify-center gap-8 flex flex-col bg-[url(patterns/triangles.webp)]">
    <div class="max-w-md mx-auto z-50 w-full px-4">
      <LastButton
        v-if="lastButton"
        v-bind="getButton(lastButton)"
      />
    </div>
    <div class="px-4 max-w-md mx-auto grid grid-cols-3 gap-4 place-content-center z-50">
      <Button
        v-for="button in buttons"
        :key="button.name"
        v-bind="button"
        @click="pressButton(button.name)"
      />
    </div>
  </div>
</template>

<style scoped>
</style>
