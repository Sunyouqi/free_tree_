<template>
  <h1>You did it!</h1>
  <p>
    Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
    documentation
  </p>
  <div id="tree_wrapper">
    <file-tree-list />
  </div>
</template>

<script setup lang="ts">
import { RemoteDriver } from 'vuefinder';
import FileTreeList from './components/FileTreeList.vue';
import "@he-tree/vue/style/default.css";
import { onMounted } from "vue";


const driver = new RemoteDriver({
  baseURL: '/api',
  url: {
    list: '/files',
    upload: '/upload',
    delete: '/delete',
    rename: '/rename',
    archive: '/archive',
    unarchive: '/unarchive',
    createFile: '/create-file',
    createFolder: '/create-folder',
    search: '/search',
    preview: '/preview',
    copy: '/copy',
    move: '/move',
    save: '/save',
    download: '/download',
  },
});

onMounted(() => { });
</script>

<style scoped>
#tree_wrapper{
  position: absolute;
  height: 80vh;
}
</style>
