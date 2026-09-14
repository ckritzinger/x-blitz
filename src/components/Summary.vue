<script setup>
const props = defineProps({
  score: { type: Number, required: true },
  previousBest: { type: Number, required: true },
})
const emit = defineEmits(['play-again', 'home'])

const isNewBest = props.score > props.previousBest
</script>

<template>
  <div class="flex min-h-screen flex-col items-center justify-center bg-slate-50 px-4 py-10 text-center">
    <div v-if="isNewBest" class="text-lg font-extrabold text-amber-500">🎉 New personal best!</div>
    <div v-else class="text-lg font-semibold text-slate-400">Run complete</div>

    <div class="mt-4 text-6xl font-extrabold text-slate-800">{{ score }}</div>
    <p class="mt-2 text-slate-500">
      Previous best: <span class="font-bold text-slate-700">{{ previousBest }}</span>
    </p>

    <div class="mt-8 flex w-full max-w-xs flex-col gap-3">
      <button
        @click="emit('play-again')"
        class="rounded-2xl bg-indigo-500 py-4 text-xl font-extrabold text-white shadow-md transition hover:bg-indigo-600 active:scale-95"
      >
        Play again
      </button>
      <button
        @click="emit('home')"
        class="rounded-2xl bg-white py-3 font-semibold text-slate-600 shadow-sm transition hover:bg-slate-100"
      >
        Home
      </button>
    </div>
  </div>
</template>
