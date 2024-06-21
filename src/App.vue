<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated style="background-color: skyblue;">
      <q-toolbar>
        <q-toolbar-title>
          Navigation
        </q-toolbar-title>
        <q-btn :flat="!isActive('/')"
               label="Widget"
               to="/" />
        <q-btn :flat="!isActive('/portofolio')"
               label="Portofolio"
               to="/portofolio" />
        <q-btn :flat="!isActive('/tugas2')"
               label="Tugas 2"
               to="/tugas2" />
        <q-btn :flat="!isActive('/tugas3')"
               label="Tugas 3"
               to="/tugas3" />
        <q-btn :flat="!isActive('/tugas4')"
               label="Tugas 4"
               to="/tugas4" />
        <q-btn :flat="!isActive('/tugas5')"
               label="Tugas 5"
               to="/tugas5" />
        <q-btn :flat="!isActive('/tugas6')"
               label="Tugas 6"
               to="/tugas6" />
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { useRouter } from 'vue-router'
const router = useRouter()

const isActive = (path) => {
  return router.currentRoute.value.path === path
}
</script>

<style lang="scss">

body, html {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
}

.q-layout {
  height: 100%;
}

.q-page-container {
  height: calc(100vh - 56px);
}
</style>
