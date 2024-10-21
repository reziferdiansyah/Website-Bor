<template>
    <div>
    <!-- PRODUCT LIST -->
    <Products/>
  </div>  
</template>

<script setup>
import Products from "./pages/products/index.vue"

definePageMeta({
  layout: 'homepage'
})
</script>