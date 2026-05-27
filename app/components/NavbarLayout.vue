<template>
  <header
    class="fixed top-4 left-1/2 -translate-x-1/2 z-50 w-fit"
    role="banner"
  >
    <nav
      class="flex items-center gap-1.5 bg-white/90 dark:bg-gray-950/90 backdrop-blur-md border border-gray-200/80 dark:border-gray-800/60 rounded-full px-2.5 py-1.5 shadow-sm shadow-black/5"
      aria-label="Navegação principal"
    >
      <!-- Logo -->
      <NuxtLink
        to="/"
        class="flex items-center gap-2 pr-3 mr-1 border-r border-gray-200 dark:border-gray-800 group"
      >
        <div
          class="w-7 h-7 rounded-lg bg-gray-100 dark:bg-gray-800 border border-gray-200 dark:border-gray-700 flex items-center justify-center overflow-hidden flex-shrink-0"
        >
          <UColorModeImage
            light="/logo-s_fundo.png"
            dark="/logo-branco-s_fundo.png"
            alt="Logo"
            class="w-full h-full object-contain"
          />
        </div>
        <span
          class="text-[13px] font-medium text-gray-700 dark:text-gray-300 whitespace-nowrap hidden md:block group-hover:text-gray-900 dark:group-hover:text-white transition-colors"
        >
          Ezequiel H. G. Müller
        </span>
      </NuxtLink>

      <!-- Nav links -->
      <div class="flex items-center gap-0.5">
        <button
          v-for="item in navItems"
          :key="item.hash"
          type="button"
          class="flex items-center gap-1.5 px-3 py-1.5 rounded-full text-[13px] font-medium text-gray-500 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all duration-150 whitespace-nowrap cursor-pointer"
          :class="{
            'bg-gray-100 dark:bg-gray-800/70 !text-gray-900 dark:!text-white':
              activeSection === item.hash,
          }"
          @click="scrollTo(item.hash)"
        >
          <UIcon :name="item.icon" class="w-3.5 h-3.5 flex-shrink-0" />
          <span class="hidden sm:block">{{ item.label }}</span>
        </button>
      </div>

      <!-- Divider -->
      <div
        class="w-px h-5 bg-gray-200 dark:bg-gray-800 mx-1 flex-shrink-0"
        aria-hidden="true"
      />

      <!-- Social icons -->
      <div class="flex items-center gap-0.5">
        <UTooltip text="GitHub">
          <UButton
            color="neutral"
            variant="ghost"
            size="xs"
            to="https://github.com/ezequielhgm"
            target="_blank"
            icon="i-simple-icons-github"
            aria-label="GitHub"
            :ui="{
              base: 'rounded-full w-8 h-8 flex items-center justify-center text-gray-400 hover:text-gray-900 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all',
            }"
          />
        </UTooltip>
        <UTooltip text="LinkedIn">
          <UButton
            color="neutral"
            variant="ghost"
            size="xs"
            to="https://www.linkedin.com/in/ezequielhgm/"
            target="_blank"
            icon="entypo-social:linkedin"
            aria-label="LinkedIn"
            :ui="{
              base: 'rounded-full w-8 h-8 flex items-center justify-center text-gray-400 hover:text-blue-600 hover:bg-blue-50 dark:hover:bg-blue-950/40 transition-all',
            }"
          />
        </UTooltip>
        <UTooltip text="Instagram">
          <UButton
            color="neutral"
            variant="ghost"
            size="xs"
            to="https://www.instagram.com/ezequielhgm/"
            target="_blank"
            icon="entypo-social:instagram"
            aria-label="Instagram"
            :ui="{
              base: 'rounded-full w-8 h-8 flex items-center justify-center text-gray-400 hover:text-pink-500 hover:bg-pink-50 dark:hover:bg-pink-950/40 transition-all',
            }"
          />
        </UTooltip>
      </div>

      <!-- Divider -->
      <div
        class="w-px h-5 bg-gray-200 dark:bg-gray-800 mx-1 flex-shrink-0"
        aria-hidden="true"
      />

      <!-- Currículo + theme toggle -->
      <div class="flex items-center gap-1">
        <UButton
          to="/curriculo.pdf"
          target="_blank"
          size="xs"
          color="neutral"
          variant="outline"
          icon="i-heroicons-document-text-20-solid"
          label="Currículo"
          :ui="{
            base: 'rounded-full text-[12px] font-medium border-gray-200 dark:border-gray-700 hover:bg-gray-100 dark:hover:bg-gray-800 transition-all hidden sm:flex',
          }"
        />
        <UColorModeButton
          size="xs"
          :ui="{
            base: 'rounded-full w-8 h-8 flex items-center justify-center text-gray-400 hover:text-gray-900 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all cursor-pointer',
          }"
        />
      </div>
    </nav>
  </header>

  <div class="h-20" aria-hidden="true" />
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const navItems = [
  { label: 'Sobre mim', hash: 'sobre', icon: 'gala:portrait2' },
  { label: 'Carreira', hash: 'carreira', icon: 'clarity:briefcase-line' },
  { label: 'Projetos', hash: 'projetos', icon: 'codicon:file-submodule' },
  {
    label: 'Contato',
    hash: 'contato',
    icon: 'fluent-emoji-high-contrast:envelope',
  },
]

const activeSection = ref('')

const scrollTo = (hash: string) => {
  const el = document.getElementById(hash)
  if (!el) return

  const navbarHeight = 80
  const top = el.getBoundingClientRect().top + window.scrollY - navbarHeight
  window.scrollTo({ top, behavior: 'smooth' })
  activeSection.value = hash
}

const updateActiveSection = () => {
  const scrollY = window.scrollY + 140
  let current = ''

  for (const item of navItems) {
    const el = document.getElementById(item.hash)
    if (!el) continue
    if (el.getBoundingClientRect().top + window.scrollY <= scrollY) {
      current = item.hash
    }
  }

  activeSection.value = current
}

onMounted(() => {
  updateActiveSection()
  window.addEventListener('scroll', updateActiveSection, { passive: true })
})

onUnmounted(() => window.removeEventListener('scroll', updateActiveSection))
</script>
