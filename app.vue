<template>
  <Suspense>
    <Index />
    <template #fallback> loading... </template>
  </Suspense>
</template>
<script setup>
import Index from "./pages/[index].vue";
</script>
