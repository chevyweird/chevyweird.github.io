<template>
  <div>
    <!-- <a-scene vr-mode-ui="enabled: false" embedded arjs>
      <a-camera
        gps-projected-camera="gpsMinDistance: 5"
        rotation-reader
      ></a-camera>

      <a-entity
        material="color: red"
        geometry="primitive: torusKnot"
        gps-projected-entity-place="latitude: 54.980180; longitude: 82.859582"
        scale="1 1 1"
      ></a-entity>
    </a-scene> -->

    <a-scene
      vr-mode-ui="enabled: false"
      arjs="sourceType: webcam; videoTexture: true; debugUIEnabled: false"
      renderer="antialias: true; alpha: true"
    >
      <a-camera gps-new-camera="gpsMinDistance: 5"></a-camera>
      <a-entity
        material="color: red"
        geometry="primitive: box"
        gps-new-entity-place="latitude: 54.980180; longitude: 82.859582"
        scale="10 10 10"
      ></a-entity>
    </a-scene>
  </div>
</template>

<script setup>
import "@ar-js-org/ar.js/aframe/build/aframe-ar";
import * as THREEx from "@ar-js-org/ar.js/three.js/build/ar-threex-location-only.js";
</script>

<style scoped>
a-scene {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

* {
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
</style>
