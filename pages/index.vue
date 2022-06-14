<script setup lang="ts">
const { data } = await useAsyncData('products', () => GqlProducts({ first: 3 }))

const story = await useStoryblok("home", { version: "draft" });
</script>

<template>
  <div>
    <HeroBanner
      :title="story.content.body[0].title"
      :image="story.content.body[0].image.filename"
      :subtitle="story.content.body[0].subtitle"
    />
    <StoryblokComponent v-if="story" :blok="story.content" />
    <ProductList :products="data.products.edges"/>
  </div>
</template>