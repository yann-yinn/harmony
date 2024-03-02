<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import PianoKeyboard from './components/PianoKeyboard.vue'
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </header>
  <PianoKeyboard msg="You did it!" />
  <RouterView />
</template>
