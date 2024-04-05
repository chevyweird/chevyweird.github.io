<template>
  <div id="ARThreeJS">
    <div>window securectx {{ windowsecure }}</div>
    <div>navigator{{ nav }}</div>
  </div>
</template>

<script setup>
import { onMounted, computed } from "vue";

import * as THREE from "three";
import { ARButton } from "../../libs/ARBtn.js";

// import WebXRPolyfill from "webxr-polyfill";
// const polyfill = new WebXRPolyfill();
// window.polyfill = polyfill;

let camera, scene, renderer;
let mesh;

const windowsecure = computed(() => window.isSecureContext);
const nav = computed(() => navigator.xr);

init();
animate();

function init() {
  scene = new THREE.Scene();

  camera = new THREE.PerspectiveCamera(
    70,
    window.innerWidth / window.innerHeight,
    0.01,
    40
  );

  renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
  renderer.setPixelRatio(window.devicePixelRatio);
  renderer.setSize(window.innerWidth, window.innerHeight);
  // This next line is important to to enable the renderer for WebXR
  renderer.xr.enabled = true; // New!
  // container.appendChild(renderer.domElement);

  var light = new THREE.HemisphereLight(0xffffff, 0xbbbbff, 1);
  light.position.set(0.5, 1, 0.25);
  scene.add(light);

  const geometry = new THREE.IcosahedronGeometry(0.1, 1);
  const material = new THREE.MeshPhongMaterial({
    color: new THREE.Color("rgb(226,35,213)"),
    shininess: 6,
    flatShading: true,
    transparent: 1,
    opacity: 0.8,
  });

  mesh = new THREE.Mesh(geometry, material);
  mesh.position.set(0, 0, -0.5);
  scene.add(mesh);

  // Add the AR button to the body of the DOM
  document.body.appendChild(ARButton.createButton(renderer));

  window.addEventListener("resize", onWindowResize, false);
}

function onWindowResize() {
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();

  renderer.setSize(window.innerWidth, window.innerHeight);
}

function animate() {
  renderer.setAnimationLoop(render);
}

function render() {
  renderer.render(scene, camera);
}
// const scene = new THREE.Scene();
// const camera = new THREE.PerspectiveCamera(
//   75,
//   window.innerWidth / window.innerHeight,
//   0.1,
//   1000
// );

// const renderer = new THREE.WebGLRenderer();
// renderer.setSize(window.innerWidth, window.innerHeight);

// const geometry = new THREE.BoxGeometry(1, 1, 1);
// const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
// const cube = new THREE.Mesh(geometry, material);
// scene.add(cube);

// camera.position.z = 5;

// function animate() {
//   requestAnimationFrame(animate);

//   cube.rotation.x += 0.01;
//   cube.rotation.y += 0.01;

//   renderer.render(scene, camera);
// }

onMounted(() => {
  // animate();
  // console.log(ARButton);
  document.querySelector("#ARThreeJS").appendChild(renderer.domElement);
});
</script>

<style lang="scss" scoped></style>
