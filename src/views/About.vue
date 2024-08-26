<template>
  <div>
    <h1>About</h1>
  </div>
</template>

<script setup lang="ts">
import { onMounted, onActivated, onUnmounted, onDeactivated } from 'vue';

defineOptions({
  name: 'About'
})

onMounted(() => {
  console.log('[About] onMounted')
})

onUnmounted(() => {
  console.log('[About] onUnmounted')
})

onDeactivated(() => {
  console.log('[About] onDeactivated')
})

onActivated(() => {
  console.log('[About] onActivated')
})
</script>