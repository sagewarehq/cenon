<script setup>
const props = defineProps({
  name: String,
  icon: String,
});
</script>

<template>
  <div class="h-32 w-full flex flex-row rounded-lg p-2 px-8 justify-center items-center border-2 border-black gap-16">
    <img
      :src="props.icon"
      class="h-24 w-24"
    >
    <span class="text-3xl font-semibold">{{ props.name }}</span>
  </div>
</template>