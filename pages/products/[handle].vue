<script setup lang="ts">
const route = useRoute();
const { data: product } = await useAsyncData(
  `product-${route.params.handle}`,
  () => GqlProduct({ handle: route.params.handle as string })
);
const { data: related } = await useAsyncData(
  `product-related-${route.params.handle}`,
  () =>
    GqlProducts({
      first: 3,
      query: `product_type:${product.value.productByHandle.productType}`,
    })
);

const loading = ref(false)

const redirectToPayment = async () => {
  loading.value = true
  const { checkoutCreate: { checkout: { webUrl } } } = await GqlCheckout({ variantId: product.value.productByHandle.variants.edges[0].node.id })

  window.location.href = webUrl
}
</script>

<template>
  <div>
    <ProductDetail
      :title="product.productByHandle.title"
      :description="product.productByHandle.description"
      :price="`${product.productByHandle.priceRange.maxVariantPrice.amount} ${product.productByHandle.priceRange.maxVariantPrice.currencyCode}`"
      :image="product.productByHandle.images.edges[0].node.src"
      :loading="loading"
      @button-clicked="redirectToPayment"
    />
    <ProductList :products="related.products.edges"/>
  </div>
</template>
