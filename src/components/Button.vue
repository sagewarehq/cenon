<script setup>
const props = defineProps({
  name: String,
  icon: String,
});
</script>

<template>
  <button class="h-32 w-32 rounded-lg border-2 border-black shadow-lg shadow-zinc-500/100 active:shadow-sm flex flex-col justify-center items-center gap-2 pt-3">
    <img
      :src="props.icon"
      class="h-16 w-16"
    >
    <span class="font-semibold">{{ props.name }}</span>
  </button>
</template>

<style scoped>
</style>