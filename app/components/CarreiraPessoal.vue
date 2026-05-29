<template>
  <div class="flex flex-col gap-8">
    <!-- Formação -->
    <div>
      <p
        class="text-[11px] uppercase tracking-widest font-semibold text-gray-400 dark:text-gray-600 mb-4"
      >
        Formação
      </p>

      <div class="flex flex-col gap-3">
        <div
          v-for="(item, index) in timelineFormacao"
          :key="index"
          class="group flex items-start gap-4 rounded-xl border border-gray-200/80 dark:border-gray-800 bg-white/50 dark:bg-gray-900/30 hover:border-gray-300 dark:hover:border-gray-700 hover:bg-white dark:hover:bg-gray-800/60 transition-all duration-200 p-4"
        >
          <div
            class="flex-shrink-0 w-9 h-9 rounded-xl bg-gray-100 dark:bg-gray-800 border border-gray-200 dark:border-gray-700 flex items-center justify-center group-hover:border-gray-300 dark:group-hover:border-gray-600 transition-colors"
          >
            <UIcon
              :name="item.icon as string"
              class="w-4 h-4 text-gray-500 dark:text-gray-400"
            />
          </div>
          <div class="flex-1 min-w-0">
            <div class="flex items-start justify-between gap-2 flex-wrap">
              <p
                class="text-sm font-semibold text-gray-900 dark:text-gray-100 leading-snug"
              >
                {{ item.title }}
              </p>
              <span
                class="text-[11px] font-medium text-gray-400 dark:text-gray-600 whitespace-nowrap"
              >
                {{ item.date }}
              </span>
            </div>
            <p
              class="mt-1 text-xs text-gray-500 dark:text-gray-500 leading-relaxed"
            >
              {{ item.description }}
            </p>
          </div>
        </div>
      </div>
    </div>

    <!-- Experiência -->
    <div>
      <p
        class="text-[11px] uppercase tracking-widest font-semibold text-gray-400 dark:text-gray-600 mb-4"
      >
        Experiência
      </p>

      <div
        class="rounded-xl border border-gray-200/80 dark:border-gray-800 bg-white/50 dark:bg-gray-900/30 overflow-hidden"
      >
        <!-- Header da experiência -->
        <div
          class="flex items-start gap-4 p-4 md:p-5 border-b border-gray-100 dark:border-gray-800/80"
        >
          <div
            class="flex-shrink-0 w-9 h-9 rounded-xl bg-gray-100 dark:bg-gray-800 border border-gray-200 dark:border-gray-700 flex items-center justify-center"
          >
            <UIcon
              name="clarity:briefcase-line"
              class="w-4 h-4 text-gray-500 dark:text-gray-400"
            />
          </div>
          <div class="flex-1 min-w-0">
            <div class="flex items-start justify-between gap-2 flex-wrap">
              <div>
                <p
                  class="text-sm font-semibold text-gray-900 dark:text-gray-100"
                >
                  Desenvolvedor FullStack
                </p>
                <p class="text-xs text-gray-500 dark:text-gray-500 mt-0.5">
                  Gazzi Sistemas · Remoto · Tempo Integral
                </p>
              </div>
              <div class="text-right">
                <span
                  class="inline-flex items-center gap-1.5 text-[11px] font-medium text-gray-400 dark:text-gray-600"
                >
                  <span
                    class="w-1.5 h-1.5 rounded-full bg-emerald-400 flex-shrink-0"
                  />
                  Fev 2025 – presente
                </span>
                <p
                  class="text-[11px] text-gray-400 dark:text-gray-600 mt-0.5 text-right"
                >
                  {{ calcularPeriodo(1) }}
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- Descrição -->
        <div class="p-4 md:p-5 flex flex-col gap-4">
          <ul class="flex flex-col gap-2">
            <li
              class="flex items-start gap-2.5 text-sm text-gray-600 dark:text-gray-400 leading-relaxed"
            >
              <span
                class="mt-2 w-1 h-1 rounded-full bg-gray-400 dark:bg-gray-600 flex-shrink-0"
              />
              Implementação e manutenção de funcionalidades, interfaces
              intuitivas, integração entre front-end e back-end, criação de
              consultas SQL e desenvolvimento de APIs seguindo padrões
              arquiteturais.
            </li>
            <li
              class="flex items-start gap-2.5 text-sm text-gray-600 dark:text-gray-400 leading-relaxed"
            >
              <span
                class="mt-2 w-1 h-1 rounded-full bg-gray-400 dark:bg-gray-600 flex-shrink-0"
              />
              Desenvolvimento de solução para o comércio focado no varejo,
              trazendo facilidade e simplicidade para o lojista desde a compra
              até a entrega de mercadorias e gestão da loja.
            </li>
            <li
              class="flex items-start gap-2.5 text-sm text-gray-600 dark:text-gray-400 leading-relaxed"
            >
              <span
                class="mt-2 w-1 h-1 rounded-full bg-gray-400 dark:bg-gray-600 flex-shrink-0"
              />
              Responsável pelo desenvolvimento de sistemas para o setor público,
              incluindo módulos de auditoria, controle interno, fiscalização e
              almoxarifado para prefeituras municipais.
            </li>
          </ul>

          <!-- Stack -->
          <div class="flex items-center gap-2 pt-1 flex-wrap">
            <NuxtImg
              src="/stack/git.svg"
              alt="Git"
              class="w-5 h-5 object-contain opacity-70 hover:opacity-100 transition-opacity"
            />
            <NuxtImg
              src="/stack/javascript.svg"
              alt="JavaScript"
              class="w-5 h-5 object-contain opacity-70 hover:opacity-100 transition-opacity"
            />
            <NuxtImg
              src="/stack/vue.svg"
              alt="Vue"
              class="w-5 h-5 object-contain opacity-70 hover:opacity-100 transition-opacity"
            />
            <NuxtImg
              src="/stack/quasar.png"
              alt="Quasar"
              class="w-5 h-5 object-contain opacity-70 hover:opacity-100 transition-opacity"
            />
            <NuxtImg
              src="/stack/java.svg"
              alt="Java"
              class="w-5 h-5 object-contain opacity-70 hover:opacity-100 transition-opacity"
            />
            <NuxtImg
              src="/stack/postgresql.svg"
              alt="PostgreSQL"
              class="w-5 h-5 object-contain opacity-70 hover:opacity-100 transition-opacity"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { TimelineItem } from '@nuxt/ui'
import { ref } from 'vue'

const timelineFormacao = ref<TimelineItem[]>([
  {
    date: 'Fev 2025 – presente',
    title: 'Bacharelado em Ciência da Computação',
    description:
      'Universidade Regional Integrada do Alto Uruguai e das Missões – Câmpus Erechim.',
    icon: 'f7:building-columns-fill',
  },
  {
    date: 'Mar 2022 – Dez 2024',
    title: 'Técnico em Informática Integrado ao Ensino Médio',
    description:
      'Instituto Federal de Educação, Ciência e Tecnologia do Rio Grande do Sul – Câmpus Erechim.',
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
  if (anos > 0) periodo += `${anos} ano${anos > 1 ? 's' : ''}`
  if (meses > 0) {
    if (anos > 0) periodo += ' e '
    periodo += `${meses} mês${meses > 1 ? 'es' : ''}`
  }

  return periodo || 'menos de um mês'
}
</script>
