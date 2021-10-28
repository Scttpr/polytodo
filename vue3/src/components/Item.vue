<script setup lang="ts">
interface Props {
  index: number
  content: string
  checked: boolean
}

interface Emits {
  (e: 'check', index: number): void
  (e: 'remove'): void
}

const props = defineProps<Props>()
const emit = defineEmits<Emits>()

const emitRemove = () => {
  emit('remove')
}

const emitCheck = () => {
  emit('check', props.index)
}
</script>

<template>
  <li
    class="bg-amber-500 w-full rounded flex justify-between items-center px-8 py-4 my-4 transition duration-1000"
    :class="{ 'bg-lime-500': checked }"
  >
    <div>
      {{ index }} - <strong :class="{ 'line-through': checked }">{{ content }}</strong>
    </div>
    <div class="flex items-center">
      <input class="mx-4" type="checkbox" :checked="checked" @input="emitCheck">
      <button @click="emitRemove">
        <mdi-delete-outline style="font-size: 1.5em" />
      </button>
    </div>
  </li>
</template>
