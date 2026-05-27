<template>
  <!-- <div
    class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 justify-center"
  > -->
  <div class="justify-center gap-4 grid grid-cols-1 md:grid-cols-2">
    <UiCardProjeto
      v-for="projeto in projetos"
      :key="projeto.id"
      :projeto="projeto"
    />
  </div>
</template>

<script setup lang="ts">
import projetosJson from '~/data/projetos.json'
import type { Projeto } from '~/types/Projeto.ts'

const projetos: Projeto[] = projetosJson
</script>
