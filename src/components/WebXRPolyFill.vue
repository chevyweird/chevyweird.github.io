<template>
  <button id="xr-button"></button>
</template>

<script setup>
import { onMounted, computed } from "vue";
import WebXRPolyfill from "webxr-polyfill";
const polyfill = new WebXRPolyfill();
window.polyfill = polyfill;

const init = () => {
  let xrButton = document.getElementById("xr-button");
  let xrSession = null;
  let xrRefSpace = null;
  initWebXR();
  function initWebXR() {
    // our new init function
    if (navigator.xr) {
      // checks if our device supports WebXR
      navigator.xr.isSessionSupported("immersive-ar").then((supported) => {
        // we check if immersive-vr session is supported
        if (supported) {
          // if it is supported
          xrButton.disabled = false; // enable the button (makes it possible to click it)
          xrButton.textContent = "Enter VR"; // change text on the button
          xrButton.addEventListener("click", onButtonClicked); // add a new event to the button, which will run the onButtonClicked function
        }
      });
    }
  }
};

onMounted(() => {
  // debugger;
  // console.log(polyfill);
  init();
});
</script>

<style lang="scss" scoped></style>
