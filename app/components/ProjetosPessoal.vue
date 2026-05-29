<template>
  <div class="flex flex-col gap-4">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
      <UiCardProjeto
        v-for="projeto in projetos"
        :key="projeto.id"
        :projeto="projeto"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import projetosJson from '~/data/projetos.json'
import type { Projeto } from '~/types/Projeto.ts'

const projetos: Projeto[] = projetosJson
</script>
