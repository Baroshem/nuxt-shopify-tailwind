<script setup lang="ts">
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  price: {
    type: String,
    required: true,
  },
  image: {
    type: String,
    required: true,
  },
  link: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  }
})
</script>

<template>
  <div class="mx-2">
    <div class="relative rounded-lg shadow-lg">
      <NuxtLink :to="link">
        <img :src="image" class="shadow-lg rounded-lg opacity-1 hover:opacity-75 transition duration-300 ease-in-out" />
      </NuxtLink>
      <div class="p-6">
        <h5 class="font-bold text-lg mb-3">{{ title }}</h5>
        <pre class="text-gray-500 mb-4">{{ price }}</pre>
        <p>{{ description }}</p>
      </div>
    </div>
  </div>
</template>