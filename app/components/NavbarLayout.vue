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
        class="flex items-center gap-2 pr-3 mr-1 border-r border-gray-300 dark:border-gray-600 group"
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

      <!-- Desktop: Nav links -->
      <div class="hidden md:flex items-center gap-0.5">
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
          <span>{{ item.label }}</span>
        </button>
      </div>

      <!-- Desktop: Divider -->
      <div
        class="hidden md:block w-px h-5 bg-gray-300 dark:bg-gray-600 mx-1 flex-shrink-0"
        aria-hidden="true"
      />

      <!-- Desktop: Social icons -->
      <div class="hidden md:flex items-center gap-0.5">
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

      <!-- Desktop: Divider -->
      <div
        class="hidden md:block w-px h-5 bg-gray-300 dark:bg-gray-600 mx-1 flex-shrink-0"
        aria-hidden="true"
      />

      <!-- Desktop: Currículo + theme toggle -->
      <div class="hidden md:flex items-center gap-1">
        <UButton
          to="/curriculo.pdf"
          target="_blank"
          size="xs"
          color="neutral"
          variant="outline"
          icon="i-heroicons-document-text-20-solid"
          label="Currículo"
          :ui="{
            base: 'rounded-full text-[12px] font-medium border-gray-200 dark:border-gray-700 hover:bg-gray-100 dark:hover:bg-gray-800 transition-all',
          }"
        />
        <UColorModeButton
          size="xs"
          :ui="{
            base: 'rounded-full w-8 h-8 flex items-center justify-center text-gray-400 hover:text-gray-900 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all cursor-pointer',
          }"
        />
      </div>

      <!-- Mobile: theme toggle + hamburger -->
      <div class="flex md:hidden items-center gap-1">
        <UColorModeButton
          size="xs"
          :ui="{
            base: 'rounded-full w-8 h-8 flex items-center justify-center text-gray-400 hover:text-gray-900 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all cursor-pointer',
          }"
        />
        <button
          type="button"
          class="w-8 h-8 rounded-full flex items-center justify-center text-gray-500 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all cursor-pointer"
          aria-label="Menu"
          @click="menuAberto = !menuAberto"
        >
          <UIcon
            :name="
              menuAberto
                ? 'i-heroicons-x-mark-20-solid'
                : 'i-heroicons-bars-3-20-solid'
            "
            class="w-4 h-4"
          />
        </button>
      </div>
    </nav>

    <!-- Mobile dropdown menu -->
    <Transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 scale-95 -translate-y-1"
      enter-to-class="opacity-100 scale-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 scale-100 translate-y-0"
      leave-to-class="opacity-0 scale-95 -translate-y-1"
    >
      <div
        v-if="menuAberto"
        class="md:hidden absolute top-full left-1/2 -translate-x-1/2 mt-2 w-56 bg-white/95 dark:bg-gray-950/95 backdrop-blur-md border border-gray-200/80 dark:border-gray-800/60 rounded-2xl shadow-lg shadow-black/10 overflow-hidden"
      >
        <!-- Nav items -->
        <div class="p-2 flex flex-col gap-0.5">
          <button
            v-for="item in navItems"
            :key="item.hash"
            type="button"
            class="flex items-center gap-3 w-full px-3 py-2.5 rounded-xl text-sm font-medium text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all duration-150 cursor-pointer text-left"
            :class="{
              'bg-gray-100 dark:bg-gray-800/70 !text-gray-900 dark:!text-white':
                activeSection === item.hash,
            }"
            @click="navegarPara(item.hash)"
          >
            <UIcon
              :name="item.icon"
              class="w-4 h-4 flex-shrink-0 text-gray-400"
            />
            {{ item.label }}
          </button>
        </div>

        <!-- Divider -->
        <div class="h-px bg-gray-100 dark:bg-gray-800 mx-2" />

        <!-- Social + Currículo -->
        <div class="p-2 flex flex-col gap-0.5">
          <a
            href="https://github.com/ezequielhgm"
            target="_blank"
            class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-gray-600 dark:text-gray-400 hover:text-emerald-600 hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all"
          >
            <UIcon name="i-simple-icons-github" class="w-4 h-4 flex-shrink-0" />
            GitHub
          </a>
          <a
            href="https://www.linkedin.com/in/ezequielhgm"
            target="_blank"
            class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-gray-600 dark:text-gray-400 hover:text-blue-600 hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all"
          >
            <UIcon
              name="entypo-social:linkedin"
              class="w-4 h-4 flex-shrink-0"
            />
            LinkedIn
          </a>
          <a
            href="https://www.instagram.com/ezequielhgm/"
            target="_blank"
            class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-gray-600 dark:text-gray-400 hover:text-pink-500 hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all"
          >
            <UIcon
              name="entypo-social:instagram"
              class="w-4 h-4 flex-shrink-0"
            />
            Instagram
          </a>
          <a
            href="/curriculo.pdf"
            target="_blank"
            class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all"
          >
            <UIcon
              name="i-heroicons-document-text-20-solid"
              class="w-4 h-4 flex-shrink-0"
            />
            Currículo
          </a>
        </div>
      </div>
    </Transition>
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
const menuAberto = ref(false)

const scrollTo = (hash: string) => {
  const el = document.getElementById(hash)
  if (!el) return
  const top = el.getBoundingClientRect().top + window.scrollY - 80
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

const fecharMenuFora = (e: MouseEvent) => {
  const target = e.target as HTMLElement
  if (!target.closest('header')) menuAberto.value = false
}

const navegarPara = (hash: string) => {
  scrollTo(hash)
  menuAberto.value = false
}

onMounted(() => {
  updateActiveSection()
  window.addEventListener('scroll', updateActiveSection, { passive: true })
  document.addEventListener('click', fecharMenuFora)
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateActiveSection)
  document.removeEventListener('click', fecharMenuFora)
})
</script>
