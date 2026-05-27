<template>
  <div class="relative min-h-screen">
    <!-- Background grid -->
    <div
      class="pointer-events-none fixed inset-0 bg-[size:48px_48px] opacity-[0.07] dark:opacity-[0.03]"
      style="
        background-image:
          linear-gradient(to right, #94a3b8 1px, transparent 1px),
          linear-gradient(to bottom, #94a3b8 1px, transparent 1px);
      "
    />

    <!-- Hero -->
    <section
      class="relative flex flex-col items-center justify-center min-h-[90vh] px-6 text-center"
    >
      <div class="relative mb-6">
        <div
          class="absolute -inset-1 rounded-full bg-gradient-to-br from-gray-300 to-gray-100 dark:from-gray-700 dark:to-gray-900 blur-sm"
        />
        <div
          class="relative rounded-full p-[3px] bg-gradient-to-br from-gray-400 via-gray-200 to-gray-400 dark:from-gray-600 dark:via-gray-800 dark:to-gray-600"
        >
          <NuxtImg
            src="/perfil.png"
            alt="Ezequiel H. G. Müller"
            class="w-28 h-28 md:w-36 md:h-36 rounded-full object-cover ring-2 ring-white dark:ring-gray-950"
          />
        </div>
        <span
          class="absolute bottom-1 right-1 w-4 h-4 rounded-full bg-emerald-400 ring-2 ring-white dark:ring-gray-950"
        />
      </div>

      <h1
        class="text-3xl md:text-5xl font-semibold tracking-tight text-gray-900 dark:text-gray-50"
      >
        Ezequiel H. G. Müller
      </h1>
      <p
        class="mt-2 text-base md:text-lg text-gray-500 dark:text-gray-400 font-medium tracking-wide"
      >
        Desenvolvedor FullStack
      </p>

      <div class="flex flex-wrap justify-center gap-2 mt-5">
        <span
          v-for="tag in tags"
          :key="tag"
          class="px-3 py-1 rounded-full text-xs font-medium bg-gray-100 dark:bg-gray-800/80 text-gray-600 dark:text-gray-400 border border-gray-200/80 dark:border-gray-700/60"
        >
          {{ tag }}
        </span>
      </div>

      <div class="flex items-center gap-3 mt-6">
        <UButton
          size="md"
          color="neutral"
          variant="solid"
          icon="fluent-emoji-high-contrast:envelope"
          label="Entrar em contato"
          class="rounded-full font-medium cursor-pointer"
          @click="scrollTo('contato')"
        />
        <UButton
          size="md"
          color="neutral"
          variant="outline"
          icon="i-heroicons-document-text-20-solid"
          label="Currículo"
          to="/curriculo.pdf"
          target="_blank"
          class="rounded-full font-medium"
        />
      </div>

      <div
        class="flex flex-col items-center gap-1.5 mt-12 animate-bounce cursor-pointer"
        @click="scrollTo('sobre')"
      >
        <span
          class="text-[11px] uppercase tracking-widest font-semibold text-gray-500 dark:text-gray-400"
          >scroll</span
        >
        <UIcon
          name="i-heroicons-chevron-down-16-solid"
          class="w-5 h-5 text-gray-500 dark:text-gray-400"
        />
      </div>
    </section>

    <!-- Content -->
    <div class="max-w-4xl mx-auto px-4 pb-2">
      <section id="sobre" class="scroll-mt-24 py-6">
        <div class="flex items-center gap-2.5 mb-8">
          <span
            class="text-xs font-semibold uppercase tracking-widest text-gray-400 dark:text-gray-500"
            >Sobre mim</span
          >
          <div class="flex-1 h-px bg-gray-200 dark:bg-gray-800" />
        </div>
        <SobreMim />
      </section>

      <section id="carreira" class="scroll-mt-24 py-6">
        <div class="flex items-center gap-2.5 mb-8">
          <span
            class="text-xs font-semibold uppercase tracking-widest text-gray-400 dark:text-gray-500"
            >Carreira</span
          >
          <div class="flex-1 h-px bg-gray-200 dark:bg-gray-800" />
        </div>
        <CarreiraPessoal />
      </section>

      <section id="projetos" class="scroll-mt-24 py-6">
        <div class="flex items-center gap-2.5 mb-8">
          <span
            class="text-xs font-semibold uppercase tracking-widest text-gray-400 dark:text-gray-500"
            >Projetos</span
          >
          <div class="flex-1 h-px bg-gray-200 dark:bg-gray-800" />
        </div>
        <ProjetosPessoal />
      </section>

      <section id="contato" class="scroll-mt-24 pt-6">
        <div class="flex items-center gap-2.5 mb-8">
          <span
            class="text-xs font-semibold uppercase tracking-widest text-gray-400 dark:text-gray-500"
            >Contato</span
          >
          <div class="flex-1 h-px bg-gray-200 dark:bg-gray-800" />
        </div>
        <ContatoPessoal />
      </section>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useSeoMeta } from 'nuxt/app'

useSeoMeta({
  title: 'Ezequiel H. G. Müller | Desenvolvedor FullStack',
  description:
    'Desenvolvedor FullStack com foco em Backend, venha conhecer um pouco mais sobre mim, projetos e carreira',
})

const tags = ['Java', 'JDBC', 'PostgreSQL', 'JavaScript']

const scrollTo = (hash: string) => {
  const el = document.getElementById(hash)
  if (!el) return
  const top = el.getBoundingClientRect().top + window.scrollY - 80
  window.scrollTo({ top, behavior: 'smooth' })
}
</script>
