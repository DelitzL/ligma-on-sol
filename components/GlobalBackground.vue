<template>
  <div class="background-container"></div>
</template>

<script setup>
import { onMounted } from 'vue';
import * as THREE from 'three';
import SimplexNoise from 'simplex-noise';

onMounted(() => {
  const simplex = new SimplexNoise();

  const conf = {
    fov: 75,
    cameraZ: 150,
    background: 0x000000,
    tubeRadius: 3,
    resY: 10,
    resX: 4,
    noiseCoef: 50,
    timeCoef: 50,
    mouseCoef: 50,
    heightCoef: 20,
    ambientColor: 0xcccccc,
    lightIntensity: 1,
    light1Color: 0x24f59e,
    light2Color: 0xe15040,
    light3Color: 0x1b859e,
    light4Color: 0x4cb04b,
  };

  let renderer, scene, camera, cameraCtrl;
  let width, height, cx, cy, wWidth, wHeight;
  const TMath = THREE.Math;
  let light1, light2, light3, light4;
  let objects = [];
  const noiseConf = {};
  let cscale;

  const mouse = new THREE.Vector2();

  init();

  function init() {
    renderer = new THREE.WebGLRenderer({ antialias: true });
    document.querySelector('.background-container').appendChild(renderer.domElement);
    camera = new THREE.PerspectiveCamera(conf.fov);
    camera.position.z = conf.cameraZ;
    cameraCtrl = new THREE.OrbitControls(camera);

    updateSize();
    window.addEventListener('resize', updateSize, false);

    document.addEventListener('mousemove', (e) => {
      mouse.x = (e.clientX / width) * 2 - 1;
      mouse.y = -(e.clientY / height) * 2 + 1;
    });

    initScene();
    animate();
  }

  function initScene() {
    scene = new THREE.Scene();
    if (conf.background) scene.background = new THREE.Color(conf.background);
    initLights();
    initObjects();
  }

  function initLights() {
    scene.add(new THREE.AmbientLight(conf.ambientColor));

    const lightDistance = 500;
    light1 = new THREE.PointLight(conf.light1Color, conf.lightIntensity, lightDistance);
    light2 = new THREE.PointLight(conf.light2Color, conf.lightIntensity, lightDistance);
    light3 = new THREE.PointLight(conf.light3Color, conf.lightIntensity, lightDistance);
    light4 = new THREE.PointLight(conf.light4Color, conf.lightIntensity, lightDistance);

    scene.add(light1, light2, light3, light4);
  }

  function initObjects() {
    const nx = Math.round(wWidth / conf.resX) + 1;
    const ny = Math.round(wHeight / conf.resY) + 1;
    for (let j = 0; j < ny; j++) {
      const color = chroma.random().hex();
      const tube = new Tube(-wWidth / 2, -wHeight / 2 + j * conf.resY, wWidth, nx, conf.tubeRadius, color, noiseConf);
      objects.push(tube);
      scene.add(tube.mesh);
    }
  }

  function animate() {
    requestAnimationFrame(animate);
    updateNoise();
    animateObjects();
    animateLights();
    if (cameraCtrl) cameraCtrl.update();
    renderer.render(scene, camera);
  }

  function animateObjects() {
    updateNoise();
    objects.forEach((obj) => obj.update());
  }

  function animateLights() {
    const time = Date.now() * 0.001;
    light1.position.x = Math.sin(time * 0.1) * wWidth / 2;
    light1.position.y = Math.cos(time * 0.2) * wHeight / 2;
    light2.position.x = Math.cos(time * 0.3) * wWidth / 2;
    light2.position.y = Math.sin(time * 0.4) * wHeight / 2;
    light3.position.x = Math.sin(time * 0.5) * wWidth / 2;
    light3.position.y = Math.sin(time * 0.6) * wHeight / 2;
    light4.position.x = Math.sin(time * 0.7) * wWidth / 2;
    light4.position.y = Math.cos(time * 0.8) * wHeight / 2;
  }

  function updateNoise() {
    noiseConf.coef = conf.noiseCoef * 0.00012;
    noiseConf.height = conf.heightCoef;
    noiseConf.time = Date.now() * conf.timeCoef * 0.000002;
    noiseConf.mouseX = mouse.x / 2;
    noiseConf.mouseY = mouse.y / 2;
  }

  function updateSize() {
    width = window.innerWidth;
    height = window.innerHeight;
    renderer.setSize(width, height);
    camera.aspect = width / height;
    camera.updateProjectionMatrix();
    const wsize = getRendererSize();
    wWidth = wsize[0];
    wHeight = wsize[1];
  }

  function getRendererSize() {
    const cam = new THREE.PerspectiveCamera(camera.fov, camera.aspect);
    const vFOV = (cam.fov * Math.PI) / 180;
    const height = 2 * Math.tan(vFOV / 2) * Math.abs(conf.cameraZ);
    const width = height * cam.aspect;
    return [width, height];
  }
});
</script>

<style scoped>
.background-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1; /* Keep the background behind other content */
}
</style>
