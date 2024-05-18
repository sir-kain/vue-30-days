<script setup lang="ts">
import type { KeyType } from '@/types/KeyboardKey'
import { onMounted } from 'vue'

defineProps<{
  keyboardKey: KeyType
}>()

function removeTransition(e: TransitionEvent) {
  console.log('e ==>', e);
  if (e.propertyName !== 'transform') return
  (e.target as HTMLElement).classList.remove('playing')
}

function playSound(e: KeyboardEvent) {
  const audio: HTMLAudioElement | null = document.querySelector(`audio[data-key="${e.code}"]`)
  const key = document.querySelector(`div[data-key="${e.code}"]`)
  if (!audio || !key) return

  key.classList.add('playing')
  audio.currentTime = 0
  audio.play()
}

onMounted(() => {
  window.addEventListener('keydown', playSound)
})
</script>

<template>
  <div :data-key="keyboardKey.code" class="key" @transitionend="removeTransition">
    <kbd>{{ keyboardKey.id.toUpperCase() }}</kbd>
    <span class="sound">{{ keyboardKey.name }}</span>
    <audio :data-key="keyboardKey.code" :src="keyboardKey.sound"></audio>
  </div>
</template>
