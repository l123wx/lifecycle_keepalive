<template>
  <div>
    <h1>Home</h1>
  </div>
</template>


<script setup lang="ts">
import { onActivated, onMounted, onUnmounted, onDeactivated } from 'vue';

defineOptions({
  name: 'Home'
})

onMounted(() => {
  console.log('[Home] onMounted')
})

onUnmounted(() => {
  console.log('[Home] onUnmounted')
})

onDeactivated(() => {
  console.log('[Home] onDeactivated')
})

onActivated(() => {
  console.log('[Home] onActivated')
})
</script>