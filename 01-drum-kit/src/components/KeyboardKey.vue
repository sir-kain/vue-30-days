<script setup lang="ts">
import type { KeyType } from '@/types/KeyboardKey'

defineProps<{
  keyboardKey: KeyType
}>()
</script>

<template>
  <div :data-key="keyboardKey.id" class="key">
    <kbd>{{ keyboardKey.id.toUpperCase() }}</kbd>
    <span class="sound">{{ keyboardKey.name }}</span>
    <audio :data-key="keyboardKey.id" :src="keyboardKey.sound"></audio>
  </div>
</template>
