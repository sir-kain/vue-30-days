<script setup lang="ts">
import { onMounted } from 'vue'
import KeyboardKey from './components/KeyboardKey.vue'
import type { KeyType } from './types/KeyboardKey'

const keys: KeyType[] = [
  {
    id: 'a',
    name: 'clap',
    sound: 'sounds/clap.wav'
  },
  {
    id: 's',
    name: 'hihat',
    sound: 'sounds/hihat.wav'
  },
  {
    id: 'd',
    name: 'kick',
    sound: 'sounds/kick.wav'
  },
  {
    id: 'f',
    name: 'openhat',
    sound: 'sounds/openhat.wav'
  },
  {
    id: 'g',
    name: 'boom',
    sound: 'sounds/boom.wav'
  },
  {
    id: 'h',
    name: 'ride',
    sound: 'sounds/ride.wav'
  },
  {
    id: 'j',
    name: 'snare',
    sound: 'sounds/snare.wav'
  },
  {
    id: 'k',
    name: 'tom',
    sound: 'sounds/tom.wav'
  },
  {
    id: 'l',
    name: 'tink',
    sound: 'sounds/tink.wav'
  }
]

function removeTransition(e) {
  if (e.propertyName !== 'transform') return
  e.target.classList.remove('playing')
}

function playSound(e: KeyboardEvent) {
  const audio: HTMLAudioElement | null = document.querySelector(`audio[data-key="${e.key}"]`)
  const key = document.querySelector(`div[data-key="${e.key}"]`)
  if (!audio || !key) return

  key.classList.add('playing')
  audio.currentTime = 0
  audio.play()
}

onMounted(() => {
  window.addEventListener('keydown', playSound)
  document
    .querySelectorAll('.key')
    .forEach((key) => key.addEventListener('transitionend', removeTransition))
})
</script>

<template>
  <div class="keys">
    <KeyboardKey v-for="key in keys" :key="key.id" :keyboardKey="key" />
  </div>
</template>
