<script setup lang="ts">
const { data } = await useAsyncData('products', () => GqlProducts({ first: 3 }))
</script>

<template>
  <div>
    <HeroBanner />
    <ProductList :products="data.products.edges"/>
  </div>
</template>