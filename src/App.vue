<template>
  <keep-alive :include="cacheList">
    <component :is="views[activeViewName]" :key="activeViewName" />
  </keep-alive>

  <div v-if="showCacheList">Include List: [ {{ cacheList.join(',') }} ]</div>
  <br>
  <div>Active View: {{ activeViewName }}</div>
  <br>

  <div>
    <input id="showCacheList" type="checkbox" v-model="showCacheList" />
    <label for="showCacheList">showCacheList</label>
  </div>
  <br>

  <div style="display: flex; gap: 10px">
    <button @click="() => activeViewName = 'Home'" class="link">Home</button>
    <button @click="() => activeViewName = 'About'" class="link">About</button>
    <button @click="handleCleanCacheList">Clean keep alive include List</button>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive, KeepAlive, watch } from 'vue';

import Home from './views/Home.vue';
import About from './views/About.vue';

const activeViewName = ref('Home')
const showCacheList = ref(false)

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
