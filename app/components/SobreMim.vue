<template>
  <div class="flex flex-col items-center mt-8 px-4 sm:px-6 md:px-10">
    <!-- sobre mim -->
    <div
      class="text-center border-gray-400 dark:border-gray-700 border-2 rounded-2xl shadow-sm backdrop-blur-sm w-full max-w-3xl p-6"
    >
      <h1 class="text-[22px] font-medium md:text-2xl mb-4">Sobre mim</h1>
      <p class="leading-relaxed">
        Olá! Sou
        <span class="font-bold text-secondary"
          >Sou Desenvolvedor Full Stack com prioridade em back-end</span
        >, atuando no desenvolvimento de sistemas web utilizando Java no
        back-end e Vue.js no front-end. Tenho experiência profissional em
        sistemas legados, trabalhando com implementação e manutenção de
        funcionalidades, integração entre camadas, construção de APIs REST,
        criação de consultas SQL e evolução de sistemas seguindo padrões
        arquiteturais já estabelecidos.
        <span class="font-bold"
          >Atualmente, estou aprofundando meus conhecimentos em Java com foco em
          Spring Boot e arquitetura de back-end moderno.
        </span>
      </p>
    </div>
    <!-- habilidades -->
    <div class="mt-10 w-full max-w-5xl">
      <h1 class="text-center text-[22px] font-medium md:text-2xl mb-6">
        Tecnologias
      </h1>

      <div
        class="grid grid-cols-3 sm:grid-cols-4 md:grid-cols-6 gap-3 items-center justify-center"
      >
        <div
          v-for="(hab, idx) in habilidades"
          :key="idx"
          class="group flex flex-col items-center justify-center gap-2 p-3 rounded-xl bg-white/40 dark:bg-gray-900/40 border border-gray-200/60 dark:border-gray-700/60 backdrop-blur-md transition-all duration-300 ease-out hover:-translate-y-1 hover:shadow-lg hover:border-gray-300 dark:hover:border-gray-600"
        >
          <NuxtImg
            :src="hab.src"
            :alt="hab.label"
            class="w-9 h-9 object-contain transition-transform duration-300 group-hover:scale-110"
          />

          <span
            class="text-xs font-medium text-gray-700/80 dark:text-gray-300/80 tracking-wide"
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
  { label: 'PostgreSQL', src: '/stack/postgresql.svg' },
  { label: 'MySQL', src: '/stack/mysql.png' },
  { label: 'JavaScript', src: '/stack/javascript.svg' },
  { label: 'TypeScript', src: '/stack/typescript.svg' },
  { label: 'Vue.js', src: '/stack/vue.svg' },
  { label: 'Quasar Framework', src: '/stack/quasar.png' },
  { label: 'TailwindCSS', src: '/stack/tailwindcss.svg' },
]
</script>
<style scoped>
.text-primary-600 {
  color: #3b82f6;
  /* Azul Tailwind */
}
</style>
