<template>
  <div
    class="group flex flex-col rounded-xl border border-gray-200/80 dark:border-gray-800 bg-white/50 dark:bg-gray-900/30 hover:border-gray-300 dark:hover:border-gray-700 hover:bg-white dark:hover:bg-gray-800/60 transition-all duration-200 overflow-hidden"
  >
    <!-- Header -->
    <div
      class="flex items-center gap-3 px-4 py-3 border-b border-gray-100 dark:border-gray-800/80"
    >
      <div
        class="flex-shrink-0 w-7 h-7 rounded-lg bg-gray-100 dark:bg-gray-800 border border-gray-200 dark:border-gray-700 flex items-center justify-center overflow-hidden"
      >
        <NuxtImg
          :src="projeto.imagemPrincipal"
          :alt="projeto.titulo"
          class="w-full h-full object-contain"
        />
      </div>
      <span
        class="text-sm font-semibold text-gray-900 dark:text-gray-100 truncate"
      >
        {{ projeto.titulo }}
      </span>
    </div>

    <!-- Body -->
    <div class="flex flex-col flex-1 p-4 gap-4">
      <!-- Descrição -->
      <p
        class="text-sm text-gray-600 dark:text-gray-400 leading-relaxed flex-1"
      >
        {{ projeto.descricao }}
      </p>

      <!-- Stack -->
      <div class="flex items-center gap-2 flex-wrap">
        <NuxtImg
          v-for="tech in projeto.stack"
          :key="tech.nome"
          :src="tech.icon"
          :alt="tech.nome"
          class="w-5 h-5 object-contain opacity-60 hover:opacity-100 transition-opacity"
        />
      </div>

      <!-- Actions -->
      <div class="flex items-center gap-2 pt-1">
        <UModal title="Imagens do Projeto" :close="{ class: 'cursor-pointer' }">
          <UButton
            size="xs"
            color="neutral"
            variant="outline"
            icon="entypo:camera"
            label="Imagens"
            :ui="{
              base: 'rounded-full text-[12px] font-medium border-gray-200 dark:border-gray-700 hover:border-yellow-500 hover:text-yellow-500 transition-all cursor-pointer',
            }"
          />
          <template #body>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2">
              <div
                v-for="(img, index) in projeto.imagens"
                :key="index"
                class="flex items-center justify-center rounded-xl overflow-hidden"
              >
                <NuxtImg
                  :src="img"
                  :alt="projeto.titulo"
                  :class="projeto.classImg"
                  class="w-full max-h-[620px] object-contain"
                  loading="lazy"
                />
              </div>
            </div>
          </template>
        </UModal>

        <UButton
          size="xs"
          color="neutral"
          variant="outline"
          :to="projeto.github"
          target="_blank"
          icon="i-simple-icons-github"
          label="GitHub"
          :ui="{
            base: 'rounded-full text-[12px] font-medium border-gray-200 dark:border-gray-700 hover:border-emerald-500 hover:text-emerald-500 transition-all',
          }"
        />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Projeto } from '~/types/Projeto.ts'

defineProps<{ projeto: Projeto }>()
</script>
