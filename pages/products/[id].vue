<template>
  <div>
    <Head>
      <Title>Nuxt Dojo | {{ product.title }}</Title>
    </Head>
    <ProductDetails :product="product" />
  </div>
</template>

<script setup>
const { id } = useRoute().params;

definePageMeta({
  layout: "products",
});

const { data: product } = await useFetch(
  `https://fakestoreapi.com/products/${id}`
);

if (!product.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "Product not found",
    fatal: true,
  });
}
</script>

<style scoped></style>
`
