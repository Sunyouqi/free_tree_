<script setup lang="ts">
import { RemoteDriver } from 'vuefinder';
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

<template>

  <div>
    <vue-finder id="my_vuefinder" :driver="driver" :config="{
      initialPath: 'local://public',
      persist: true,
    }" />

  </div>
</template>

<style scoped>

</style>