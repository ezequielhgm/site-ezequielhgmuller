<template>
  <footer class="border-t border-gray-200/80 dark:border-gray-800 mt-8">
    <div
      class="max-w-4xl mx-auto px-4 py-6 flex flex-col sm:flex-row items-center justify-between gap-4"
    >
      <!-- Esquerda -->
      <div class="flex flex-col items-center sm:items-start gap-0.5">
        <p class="text-sm font-medium text-gray-900 dark:text-gray-100">
          Ezequiel H. G. Müller
        </p>
        <p class="text-xs text-gray-400 dark:text-gray-600">
          Transformando ideias em aplicações reais.
        </p>
      </div>

      <!-- Direita -->
      <div class="flex items-center gap-3">
        <p class="text-xs text-gray-400 dark:text-gray-600 mr-2">
          © {{ new Date().getFullYear() }}
        </p>

        <div class="w-px h-4 bg-gray-200 dark:bg-gray-800" />

        <div class="flex items-center gap-0.5">
          <UButton
            color="neutral"
            variant="ghost"
            size="xs"
            to="https://github.com/ezequielhgm"
            target="_blank"
            icon="i-simple-icons-github"
            aria-label="GitHub"
            :ui="{
              base: 'rounded-full w-8 h-8 flex items-center justify-center text-gray-400 hover:text-emerald-500 hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all',
            }"
          />
          <UButton
            color="neutral"
            variant="ghost"
            size="xs"
            to="https://www.linkedin.com/in/ezequielhgm/"
            target="_blank"
            icon="entypo-social:linkedin"
            aria-label="LinkedIn"
            :ui="{
              base: 'rounded-full w-8 h-8 flex items-center justify-center text-gray-400 hover:text-blue-500 hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all',
            }"
          />
          <UButton
            color="neutral"
            variant="ghost"
            size="xs"
            to="https://www.instagram.com/ezequielhgm/"
            target="_blank"
            icon="entypo-social:instagram"
            aria-label="Instagram"
            :ui="{
              base: 'rounded-full w-8 h-8 flex items-center justify-center text-gray-400 hover:text-pink-500 hover:bg-gray-100 dark:hover:bg-gray-800/70 transition-all',
            }"
          />
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts"></script>
