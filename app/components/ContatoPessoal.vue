<template>
  <div class="flex flex-col gap-3">
    <!-- Email -->
    <div
      class="group flex items-center gap-4 rounded-xl border border-gray-200/80 dark:border-gray-800 bg-white/50 dark:bg-gray-900/30 hover:border-yellow-400/50 dark:hover:border-yellow-500/30 hover:bg-white dark:hover:bg-gray-800/60 transition-all duration-200 px-4 py-3 cursor-pointer"
      @click="copiarEmail"
    >
      <div
        class="flex-shrink-0 w-9 h-9 rounded-xl bg-gray-100 dark:bg-gray-800 border border-gray-200 dark:border-gray-700 flex items-center justify-center group-hover:border-yellow-400/50 dark:group-hover:border-yellow-500/40 transition-colors"
      >
        <UIcon
          :name="emailCopiado ? 'i-lucide-check' : 'i-lucide-mail'"
          :class="
            emailCopiado
              ? 'text-emerald-400'
              : 'text-gray-500 dark:text-gray-400 group-hover:text-yellow-500 dark:group-hover:text-yellow-400'
          "
          class="w-4 h-4 transition-colors"
        />
      </div>
      <div class="flex-1 min-w-0">
        <p
          class="text-[11px] font-medium text-gray-400 dark:text-gray-600 uppercase tracking-widest"
        >
          E-mail
        </p>
        <p
          class="text-sm font-semibold text-gray-900 dark:text-gray-100 truncate"
        >
          ezequielhgm@gmail.com
        </p>
      </div>
      <div class="flex items-center gap-1.5 flex-shrink-0">
        <span
          v-if="emailCopiado"
          class="text-[11px] font-medium text-emerald-400"
        >
          Copiado!
        </span>
        <span
          v-else
          class="text-[11px] font-medium text-yellow-500 dark:text-yellow-400 opacity-0 group-hover:opacity-100 transition-opacity"
        >
          Clique para copiar
        </span>
        <UIcon
          name="i-lucide-copy"
          class="w-3.5 h-3.5 text-yellow-500 dark:text-yellow-400 opacity-0 group-hover:opacity-100 transition-opacity"
        />
      </div>
    </div>

    <!-- Links sociais -->
    <a
      v-for="link in links"
      :key="link.label"
      :href="link.href"
      target="_blank"
      rel="noopener noreferrer"
      class="group flex items-center gap-4 rounded-xl border border-gray-200/80 dark:border-gray-800 bg-white/50 dark:bg-gray-900/30 hover:bg-white dark:hover:bg-gray-800/60 transition-all duration-200 px-4 py-3"
      :class="link.hoverBorder"
    >
      <div
        class="flex-shrink-0 w-9 h-9 rounded-xl bg-gray-100 dark:bg-gray-800 border border-gray-200 dark:border-gray-700 flex items-center justify-center transition-colors"
        :class="link.hoverIconBg"
      >
        <UIcon :name="link.icon" :class="link.iconColor" class="w-4 h-4" />
      </div>
      <div class="flex-1 min-w-0">
        <p
          class="text-[11px] font-medium text-gray-400 dark:text-gray-600 uppercase tracking-widest"
        >
          {{ link.label }}
        </p>
        <p
          class="text-sm font-semibold text-gray-900 dark:text-gray-100 truncate group-hover:transition-colors"
          :class="link.hoverText"
        >
          {{ link.handle }}
        </p>
      </div>
      <UIcon
        name="i-lucide-arrow-right"
        class="w-4 h-4 flex-shrink-0 opacity-0 group-hover:opacity-100 group-hover:translate-x-0.5 transition-all duration-200"
        :class="link.iconColor"
      />
    </a>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const toast = useToast()
const emailCopiado = ref(false)

const links = [
  {
    label: 'GitHub',
    handle: 'ezequielhgm',
    href: 'https://github.com/ezequielhgm',
    icon: 'i-simple-icons-github',
    iconColor: 'text-gray-500 dark:text-gray-400 group-hover:text-emerald-500',
    hoverBorder: 'hover:border-emerald-500/40 dark:hover:border-emerald-500/30',
    hoverIconBg: 'group-hover:border-emerald-500/40',
    hoverText: 'group-hover:text-emerald-500',
  },
  {
    label: 'LinkedIn',
    handle: 'ezequielhgm',
    href: 'https://www.linkedin.com/in/ezequielhgm',
    icon: 'entypo-social:linkedin',
    iconColor: 'text-gray-500 dark:text-gray-400 group-hover:text-blue-500',
    hoverBorder: 'hover:border-blue-500/40 dark:hover:border-blue-500/30',
    hoverIconBg: 'group-hover:border-blue-500/40',
    hoverText: 'group-hover:text-blue-500',
  },
  {
    label: 'Instagram',
    handle: '@ezequielhgm',
    href: 'https://instagram.com/ezequielhgm',
    icon: 'entypo-social:instagram',
    iconColor: 'text-gray-500 dark:text-gray-400 group-hover:text-pink-500',
    hoverBorder: 'hover:border-pink-500/40 dark:hover:border-pink-500/30',
    hoverIconBg: 'group-hover:border-pink-500/40',
    hoverText: 'group-hover:text-pink-500',
  },
]

const copiarEmail = async () => {
  try {
    await navigator.clipboard.writeText('ezequielhgm@gmail.com')
    emailCopiado.value = true
    toast.add({ color: 'success', title: 'E-mail copiado!', duration: 2000 })
    setTimeout(() => {
      emailCopiado.value = false
    }, 2000)
  } catch {
    toast.add({
      color: 'error',
      title: 'Erro ao copiar e-mail',
      duration: 2000,
    })
  }
}
</script>
