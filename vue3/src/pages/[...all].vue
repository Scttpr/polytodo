<script setup lang="ts">
const router = useRouter()
</script>

<template>
  <p class="text-4xl text-lime-600 font-bold my-4">
    Not Found
  </p>
  <button class="py-2 px-8 bg-lime-600 rounded" @click="router.back()">
    Back
  </button>
</template>
