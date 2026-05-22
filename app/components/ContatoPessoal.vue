<template>
  <div class="flex justify-center mt-4 mb-4">
    <h1 class="text-[22px] md:text-2xl font-medium text-center">
      Formas de Contato
    </h1>
  </div>

  <div class="flex justify-center px-4 md:px-0">
    <div class="w-full max-w-6xl">
      <UCard variant="subtle" class="flex flex-col rounded-2xl">
        <div class="flex justify-center flex-col md:flex-row gap-6">
          <!-- github-->
          <a
            href="https://github.com/ezequielhgmuller"
            target="_blank"
            rel="noopener noreferrer"
            class="flex items-center gap-4 transition-all duration-300 hover:translate-x-2 cursor-pointer group"
          >
            <UIcon
              name="i-simple-icons-github"
              class="size-6 text-green-600 group-hover:scale-110 transition-transform"
            />
            <div class="flex-1">
              <p class="text-sm font-medium text-gray-500">GitHub</p>
              <p
                class="font-semibold text-gray-900 dark:text-white group-hover:text-green-600 transition-colors"
              >
                ezequielhgmuller
              </p>
            </div>
            <UIcon
              name="i-lucide-arrow-right"
              class="size-5 text-green-600 opacity-0 group-hover:opacity-100 transition-opacity"
            />
          </a>

          <!-- linkedIn -->
          <a
            href="https://www.linkedin.com/in/ezequielhgmuller"
            target="_blank"
            rel="noopener noreferrer"
            class="flex items-center gap-4 transition-all duration-300 hover:translate-x-2 cursor-pointer group"
          >
            <UIcon
              name="entypo-social:linkedin"
              class="size-6 text-blue-600 group-hover:scale-110 transition-transform"
            />
            <div class="flex-1">
              <p class="text-sm font-medium text-gray-500">LinkedIn</p>
              <p
                class="font-semibold text-gray-900 dark:text-white group-hover:text-blue-600 transition-colors"
              >
                ezequielhgmuller
              </p>
            </div>
            <UIcon
              name="i-lucide-arrow-right"
              class="size-5 text-blue-600 opacity-0 group-hover:opacity-100 transition-opacity"
            />
          </a>

          <!-- instagram -->
          <a
            href="https://instagram.com/ezequielhgmuller"
            target="_blank"
            rel="noopener noreferrer"
            class="flex items-center gap-4 transition-all duration-300 hover:translate-x-2 cursor-pointer group"
          >
            <UIcon
              name="entypo-social:instagram"
              class="size-6 text-pink-500 group-hover:scale-110 transition-transform"
            />
            <div class="flex-1">
              <p class="text-sm font-medium text-gray-500">Instagram</p>
              <p
                class="font-semibold text-gray-900 dark:text-white group-hover:text-pink-500 transition-colors"
              >
                @ezequielhgmuller
              </p>
            </div>
            <UIcon
              name="i-lucide-arrow-right"
              class="size-5 text-pink-500 opacity-0 group-hover:opacity-100 transition-opacity"
            />
          </a>

          <!-- email -->
          <div
            @click="copiarEmail"
            class="flex items-center gap-4 transition-all duration-300 hover:translate-x-2 cursor-pointer group"
          >
            <div class="flex items-center gap-2">
              <UIcon
                v-if="emailCopiado"
                name="i-lucide-check"
                class="size-5 text-green-500 animate-pulse"
              />
              <UIcon
                v-else
                name="i-lucide-copy"
                class="size-5 text-gray-400 opacity-0 group-hover:opacity-100 transition-opacity"
              />
            </div>
          </div>
        </div>
      </UCard>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const toast = useToast()

const emailCopiado = ref(false)

// Funções email ----
const copiarEmail = async () => {
  try {
    await navigator.clipboard.writeText('zikimuller017@gmail.com')
    emailCopiado.value = true
    toast.add({
      color: 'success',
      title: 'E-mail copiado!',
      duration: 2000,
    })
    setTimeout(() => {
      emailCopiado.value = false
    }, 2000)
  } catch (err) {
    console.error('Erro ao copiar email:', err)
    toast.add({
      color: 'error',
      title: 'Erro ao copiar e-mail',
      duration: 2000,
    })
  }
}
</script>
