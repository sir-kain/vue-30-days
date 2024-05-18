<script setup lang="ts">
import KeyboardKey from './components/KeyboardKey.vue'
import type { KeyType } from './types/KeyboardKey'

const keys: KeyType[] = [
  {
    id: 'a',
    code: 'KeyA',
    name: 'clap',
    sound: 'sounds/clap.wav'
  },
  {
    id: 's',
    code: 'KeyS',
    name: 'hihat',
    sound: 'sounds/hihat.wav'
  },
  {
    id: 'd',
    code: 'KeyD',
    name: 'kick',
    sound: 'sounds/kick.wav'
  },
  {
    id: 'f',
    code: 'KeyF',
    name: 'openhat',
    sound: 'sounds/openhat.wav'
  },
  {
    id: 'g',
    code: 'KeyG',
    name: 'boom',
    sound: 'sounds/boom.wav'
  },
  {
    id: 'h',
    code: 'KeyH',
    name: 'ride',
    sound: 'sounds/ride.wav'
  },
  {
    id: 'j',
    code: 'KeyJ',
    name: 'snare',
    sound: 'sounds/snare.wav'
  },
  {
    id: 'k',
    code: 'KeyK',
    name: 'tom',
    sound: 'sounds/tom.wav'
  },
  {
    id: 'l',
    code: 'KeyL',
    name: 'tink',
    sound: 'sounds/tink.wav'
  }
]
</script>

<template>
  <div class="keys">
    <KeyboardKey v-for="key in keys" :key="key.id" :keyboardKey="key" />
  </div>
</template>
