<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar class="bg-green-7">
        <q-toolbar-title> AR Mobile</q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import WebXRPolyfill from "webxr-polyfill";
window.polyfill = new WebXRPolyfill();
</script>
