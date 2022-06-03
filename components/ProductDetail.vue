<script setup lang="ts">
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  description: {
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
  loading: {
    type: Boolean,
    required: true
  }
});

const emit = defineEmits(['button-clicked'])
</script>

<template>
  <section>
    <div class="grid grid-cols-2 flex items-center px-20">
      <img
        :src="image"
        class="rounded-lg shadow-lg -rotate-6"
        alt="Product Image"
      />
      <div class="rounded-lg shadow-lg p-12 backdrop-blur-2xl">
        <h2 class="text-4xl font-bold mb-6">{{ title }}</h2>
        <p class="text-gray-500 mb-6">
          {{ description }}
        </p>

        <button
          @click="emit('button-clicked')"
          class="px-7 py-3 bg-green-600 text-white font-medium text-sm rounded shadow-md hover:bg-green-700 hover:shadow-lg focus:bg-green-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-green-800 active:shadow-lg transition duration-150 ease-in-out"
        >
          {{ loading ? 'Redirecting' : `Pay ${price}` }}
        </button>
      </div>
    </div>
  </section>
</template>
