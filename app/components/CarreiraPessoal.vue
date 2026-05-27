<template>
  <!-- formação academica -->
  <div
    class="flex flex-col items-center gap-5 w-full max-w-4xl mx-auto mt-4 px-4"
  >
    <div class="w-full flex flex-col items-center">
      <div
        class="hidden md:flex flex-row items-start justify-center gap-0 w-full relative"
      >
        <div
          class="absolute top-5 left-[calc(16.66%)] right-[calc(16.66%)] h-0.5 bg-secondary/40 z-0"
        />

        <div
          v-for="(item, index) in timelineFormacao"
          :key="index"
          class="flex flex-col items-center flex-1 relative z-10"
        >
          <div
            class="flex items-center justify-center w-10 h-10 rounded-full bg-secondary/20 border-2 border-secondary text-secondary mb-3"
          >
            <UIcon :name="item.icon as string" class="size-5" />
          </div>

          <div class="text-center px-3 max-w-[220px]">
            <p class="text-xs text-muted mb-1">{{ item.date }}</p>
            <p class="font-semibold text-sm leading-snug mb-1">
              {{ item.title }}
            </p>
            <p class="text-xs text-muted leading-relaxed">
              {{ item.description }}
            </p>
          </div>
        </div>
      </div>

      <div class="md:hidden w-full flex flex-col items-center">
        <UTimeline
          :default-value="2"
          :items="timelineFormacao"
          class="w-full break-words whitespace-normal"
          color="secondary"
        />
      </div>
    </div>

    <!-- Linha 2: Experiência em linha separada -->
    <div class="w-full flex flex-col items-center">
      <UCard variant="subtle" class="w-full max-w-2xl rounded-2xl">
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="clarity:briefcase-line" class="size-5" />
            <span class="font-medium text-[17px]"
              >Gazzi Sistemas - Desenvolvedor FullStack</span
            >
          </div>
          <span class="font-normal">
            Fev de 2025 - O momento | {{ calcularPeriodo(1) }}<br />
            Remoto - Tempo Integral<br />
          </span>
        </template>
        <Placeholder>
          <div class="text-justify">
            - Trabalho na implementação e manutenção de funcionalidades,
            interfaces intuitivas, integração entre front-end e back-end,
            criação de consultas SQL e desenvolvimento de APIs seguindo padrões
            arquiteturais existentes....<br />
            - Desenvolvemos uma solução para o comércio focado no varejo
            trazendo mais facilidade e simplicidade para o logista desde a
            compra ate a entrega de mercadorias e gestão da loja. Também fui
            responsável pelo desenvolvimento de sistemas destinados ao setor
            público, incluindo módulos de auditoria, controle interno,
            fiscalização e almoxarifado para prefeituras municipais.<br />
          </div>
          <div class="flex justify-center items-center mt-2 gap-4">
            <NuxtImg src="/stack/git.svg" alt="Logo do Git" class="w-8" />
            <NuxtImg
              src="/stack/javascript.svg"
              alt="Logo do JavaScript"
              class="w-8"
            />
            <NuxtImg src="/stack/vue.svg" alt="Logo do Vue" class="w-8" />
            <NuxtImg src="/stack/quasar.png" alt="Logo do Quasar" class="w-8" />
            <NuxtImg src="/stack/java.svg" alt="Logo do Java" class="w-8" />
            <NuxtImg
              src="/stack/postgresql.svg"
              alt="Logo do PostgreSQL"
              class="w-8"
            />
          </div>
        </Placeholder>
      </UCard>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { TimelineItem } from '@nuxt/ui'
import { ref } from 'vue'

const timelineFormacao = ref<TimelineItem[]>([
  {
    date: 'Fev, 2025 - O momento',
    title: 'Bacharelado em Ciência da Computação',
    description:
      'Bacharel em Ciência da Computação pela Universidade Regional Integrada do Alto Uruguai e das Missões - Câmpus Erechim.',
    icon: 'f7:building-columns-fill',
  },
  {
    date: 'Mar, 2022 - Dez, 2024',
    title: 'Técnico em Informática Integrado ao Ensino Médio',
    description:
      'Formado em Técnico em Informática no Ensino Médio pelo Instituto Federal de Educação, Ciência e Tecnologia do Rio Grande do Sul - Câmpus Erechim',
    icon: 'heroicons-outline:academic-cap',
  },
])

const calcularPeriodo = (mes: number): string => {
  const dataInicio = new Date(2025, mes)
  const dataAtual = new Date()

  let anos = dataAtual.getFullYear() - dataInicio.getFullYear()
  let meses = dataAtual.getMonth() - dataInicio.getMonth()

  if (meses < 0) {
    anos--
    meses += 12
  }

  let periodo = ''
  if (anos > 0) {
    periodo += `${anos} ano${anos > 1 ? 's' : ''}`
  }

  if (meses > 0) {
    if (anos > 0) periodo += ' e '
    periodo += `${meses} mês${meses > 1 ? 'es' : ''}`
  }

  return periodo || 'menos de um mês'
}
</script>

<style scoped>
::v-deep .u-timeline,
::v-deep .u-timeline * {
  white-space: normal !important;
  overflow-wrap: anywhere !important;
  word-break: break-word !important;
}
</style>
