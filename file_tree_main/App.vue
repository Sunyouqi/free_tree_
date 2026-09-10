
<script setup lang="ts">

import FileTreePage from './FileTreePage.vue';
import FinderPage from './FinderPage.vue';
import PieChart from './PieChart.vue';
import Home from './Home.vue';
import "@he-tree/vue/style/default.css";
import { reactive, defineComponent, onMounted } from "vue";
import { ref, computed } from 'vue'

const routes: Record<string, unknown> = {
  '/': Home,
  '/FileTreePage': FileTreePage,
  '/FinderPage': FinderPage,
  '/PieChart': PieChart,
};

const currentPage = ref(window.location.hash)
window.addEventListener('hashchange', ()=>{
  currentPage.value = window.location.hash
})


const currentView = computed(()=>{
  return (routes as Record<string, unknown>)[currentPage.value.slice(1) || '/']
})

// Update the data when Component A emits it

onMounted(() => { });
</script>
<template>
  <h1>You did it!</h1>
  <p>
    Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
    documentation
  </p>
  <div>
<!--    <vue-finder id="my_vuefinder" :driver="driver" :config="{-->
<!--      initialPath: 'local://public',-->
<!--      persist: true,-->
<!--    }" />-->
    <a href="#/">Home</a>> |
    <a href="#/FileTreePage"> FileTreePage </a> |
    <a href="#/FinderPage"> FinderPage </a> |
    <a href="#/PieChart"> PieChart </a> |
    <a href="https://superlab.rnd.huawei.com/enveditor/#/index" target="_blank"> SuperLab </a>
    <br/>
    <component :is="currentView"></component>
  </div>
</template>

<style scoped></style>
