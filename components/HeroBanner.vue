<script setup lang="ts">
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  subtitle: {
    type: String,
    required: true,
  },
  image: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <section>
    <img
      :src="image"
      class="h-[500px] w-full"
    />

    <div class="mx-auto px-32">
      <div
        class="text-7xl font-bold text-center text-gray-800 rounded-lg shadow-lg py-16 px-12 bg-white/70 -mt-[170px] backdrop-blur-xl"
      >
        <h1 class="mb-3">{{ title }}</h1>
        <span class="text-green-600">{{ subtitle }}</span>
      </div>
    </div>
  </section>
</template>
