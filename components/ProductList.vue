<script setup lang="ts">
const props = defineProps({
  products: {
    type: undefined,
    required: true
  }
})
</script>

<template>
  <div class="flex my-20">
    <ProductCard
      v-for="product in products"
      :key="product.node.id"
      :image="product.node.images.edges[0].node.src"
      :title="product.node.title"
      :price="`${product.node.priceRange.maxVariantPrice.amount} ${product.node.priceRange.maxVariantPrice.currencyCode}`"
      :link="`/products/${product.node.handle}`"
      :description="product.node.description"
    />
  </div>
</template>