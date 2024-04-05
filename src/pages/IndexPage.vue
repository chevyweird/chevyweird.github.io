<template>
  <q-page padding class="flex justify-center">
    <q-list class="q-pa-md routes-list">
      <div class="column" style="gap: 10px">
        <q-btn outline label="AR.JS" to="/arjs" />
        <q-btn outline label="Three.js" to="/threejs" />
        <q-btn outline label="webxrpolyfill" to="/webxrpolyfill" />
      </div>
    </q-list>
  </q-page>
</template>

<script setup></script>

<style>
.routes-list {
  width: 300px;
  height: 400px;
  border-radius: 16px;
  box-shadow: 0 0 2px 0px #818181;
}
</style>
