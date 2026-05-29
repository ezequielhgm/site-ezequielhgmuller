<template>
  <div class="flex flex-col gap-10">
    <!-- Bio -->
    <div
      class="relative rounded-2xl border border-gray-200 dark:border-gray-800 bg-white/60 dark:bg-gray-900/40 backdrop-blur-sm p-6 md:p-8"
    >
      <!-- Detalhe canto -->
      <div
        class="absolute top-0 left-6 w-8 h-px bg-gray-400 dark:bg-gray-600"
      />
      <div
        class="absolute bottom-0 right-6 w-8 h-px bg-gray-400 dark:bg-gray-600"
      />

      <p
        class="text-sm md:text-base leading-relaxed text-gray-600 dark:text-gray-400"
      >
        Olá! Sou
        <span class="font-semibold text-gray-900 dark:text-gray-100">
          Desenvolvedor Full Stack com foco em Backend.
        </span>
        Formado como Técnico em Informática pelo IFRS e atualmente graduando em
        Bacharelado em Ciência da Computação pela URI. Tenho experiência no
        desenvolvimento de sistemas, atuando com
        <span class="font-medium text-gray-800 dark:text-gray-200"
          >APIs REST</span
        >,
        <span class="font-medium text-gray-800 dark:text-gray-200"
          >bancos de dados SQL</span
        >, criação de interfaces intuitivas e manutenção/evolução de software
        seguindo padrões arquiteturais.
      </p>

      <!-- Destaque atual -->
      <div
        class="mt-5 flex items-start gap-3 rounded-xl bg-gray-50 dark:bg-gray-800/60 border border-gray-200 dark:border-gray-700/60 px-4 py-3"
      >
        <span
          class="mt-0.5 w-1.5 h-1.5 rounded-full bg-emerald-400 flex-shrink-0 mt-1"
        />
        <p class="text-sm text-gray-600 dark:text-gray-400">
          <span class="font-semibold text-gray-900 dark:text-gray-100"
            >Atualmente</span
          >
          aprofundando conhecimentos em Java, com foco em
          <span class="font-medium text-gray-800 dark:text-gray-200"
            >Spring Boot</span
          >
          e arquitetura moderna de back-end.
        </p>
      </div>
    </div>

    <!-- Habilidades -->
    <div>
      <p
        class="text-[11px] uppercase tracking-widest font-semibold text-gray-400 dark:text-gray-600 mb-4"
      >
        Stack
      </p>
      <div class="grid grid-cols-4 sm:grid-cols-6 md:grid-cols-7 gap-2">
        <div
          v-for="(hab, idx) in habilidades"
          :key="idx"
          class="group flex flex-col items-center justify-center gap-2 p-3 rounded-xl border border-gray-200/80 dark:border-gray-800 bg-white/50 dark:bg-gray-900/30 hover:border-gray-300 dark:hover:border-gray-700 hover:bg-white dark:hover:bg-gray-800/60 transition-all duration-200 cursor-default"
        >
          <NuxtImg
            :src="hab.src"
            :alt="hab.label"
            class="w-8 h-8 object-contain transition-transform duration-200 group-hover:scale-110"
          />
          <span
            class="text-[11px] font-medium text-gray-500 dark:text-gray-500 group-hover:text-gray-700 dark:group-hover:text-gray-300 transition-colors text-center leading-tight"
          >
            {{ hab.label }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const habilidades = [
  { label: 'Git', src: '/stack/git.svg' },
  { label: 'Java', src: '/stack/java.svg' },
  { label: 'JavaScript', src: '/stack/javascript.svg' },
  { label: 'Vue.js', src: '/stack/vue.svg' },
  { label: 'PostgreSQL', src: '/stack/postgresql.svg' },
  { label: 'MySQL', src: '/stack/mysql.png' },
]
</script>
