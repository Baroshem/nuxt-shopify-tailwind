<template>
  <nav class="py-2 relative w-full">
    <div class="px-6 flex items-center">
      <NuxtLink to="/">
        <img class="h-20 w-20 mr-16" src="/logo.svg" alt="Store logo" />
      </NuxtLink>
      <div class="flex justify-center relative">
        <div class="mb-3 w-96">
          <input type="search" class="
                block
                w-full
                px-3
                py-1
                bg-white bg-clip-padding
                border border-solid border-gray-300
                rounded
              " id="search" placeholder="Search for products" @input="fetchSearchResults" />
        </div>
        <div v-if="hits.length" class="flex justify-center absolute top-10 z-10">
          <ul class="bg-white border border-gray-200 w-96 text-gray-900">
            <li v-for="hit in result.hits" :key="hit.objectID" class="px-6 py-2 border-b border-gray-200 w-full"
              @click="hits = []">
              <NuxtLink :to="`/products/${hit.Handle}`" class="flex items-center">
                <img class="w-20" :src="hit['Image Src']" />
                <p class="ml-4">{{ hit.Title }}</p>
              </NuxtLink>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </nav>
</template>

<script lang="ts" setup>
const { result, search } = useSearch('headless_commerce')
const hits = ref([])

const fetchSearchResults = async (e) => {
  await search({ query: e.target.value })
  hits.value = result.value.hits
}
</script>

