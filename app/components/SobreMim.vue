<template>
  <div class="flex flex-col items-center mt-4 px-4 sm:px-6 md:px-10">
    <!-- sobre mim -->
    <h1 class="text-[22px] font-medium md:text-2xl mb-4">Sobre mim</h1>

    <div
      class="text-center border-gray-400 dark:border-gray-700 border-2 rounded-2xl shadow-sm backdrop-blur-sm w-full max-w-3xl p-6"
    >
      <p class="leading-relaxed">
        Olá! Sou
        <span class="font-bold text-secondary"
          >Sou Desenvolvedor Full Stack com foco em Backend.
        </span>
        Formado como Técnico em Informática pelo IFRS e atualmente graduando em
        Bacharelado em Ciência da Computação pela URI. Tenho
        <b> experiência no desenvolvimento de sistemas</b>, atuando com
        <b>APIs REST</b>, <b>bancos de dados SQL</b>, criação de
        <b
          >interfaces intuitivas e manutenção/evolução de software seguindo
          padrões arquiteturais</b
        >.

        <span class="font-bold"
          >Atualmente, estou aprofundando meus conhecimentos em Java, com foco
          em Spring Boot e arquitetura moderna de back-end.
        </span>
      </p>
    </div>

    <!-- habilidades -->
    <div class="mt-10 w-full max-w-5xl">
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
  { label: 'JavaScript', src: '/stack/javascript.svg' },
  { label: 'Vue.js', src: '/stack/vue.svg' },
  { label: 'Quasar Framework', src: '/stack/quasar.png' },
  { label: 'PostgreSQL', src: '/stack/postgresql.svg' },
  { label: 'MySQL', src: '/stack/mysql.png' },
]
</script>
<style scoped>
.text-primary-600 {
  color: #3b82f6;
  /* Azul Tailwind */
}
</style>
