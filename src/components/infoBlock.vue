<script setup>
defineProps({
  imgUrl: String,
  title: String,
  description: String
})
</script>

<template>
  <div class="flex flex-col items-center text-center w-72 mx-auto">
    <img height="80" width="80" :src="imgUrl" alt="cart-img" />
    <h2 class="mt-4 text-2xl font-medium">{{ title }}</h2>
    <p class="text-grey-400">{{ description }}</p>
  </div>
</template>
