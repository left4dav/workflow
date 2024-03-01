<script setup>
import { VueFlow, useVueFlow } from '@vue-flow/core';
import { computed } from 'vue';
import useStore from './store.js';

const store = useStore();

const { onConnect, addEdges } = useVueFlow();

onConnect((params) => addEdges([params]));
</script>

<template>
  <VueFlow v-model="store.elements" :fit-view-on-init="true">
    <div
      style="
        position: absolute;
        right: 10px;
        top: 10px;
        z-index: 4;
        display: flex;
        gap: 0.25rem;
      "
    >
      <button @click="store.updatePosition">update positions</button>
      <button @click="store.toggleClass">toggle class</button>
      <button @click="store.log">log store state</button>
      <button @click="store.reset">reset elements</button>
    </div>
  </VueFlow>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
