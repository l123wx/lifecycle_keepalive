<template>
  <keep-alive :include="cacheList">
    <component :is="views[activeViewName]" :key="activeViewName" />
  </keep-alive>

  <div>Include List: [ {{ cacheList.join(',') }} ]</div>
  <br>

  <button @click="() => activeViewName = 'Home'" class="link">Index</button>
  <button @click="() => activeViewName = 'About'" class="link">About</button>
  <button @click="handleCleanCacheList">Clean keep alive include List</button>
</template>

<script setup lang="ts">
import { ref, reactive, KeepAlive, watch } from 'vue';

import Home from './views/Home.vue';
import About from './views/About.vue';

const activeViewName = ref('Home')

const views: Record<string, any> = {
  Home,
  About
}

const cacheList = reactive(['Home'])

const handleCleanCacheList = () => {
  cacheList.splice(0, 1)
}

watch(() => cacheList, () => {
  console.log(cacheList)
}, {
  deep: true
})
</script>
