<script setup>
import { onBeforeUnmount, onMounted, ref } from 'vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'
import siteContent from '../content/siteContent'

const isMenuOpen = ref(false)
const hasScrolled = ref(false)

const handleScroll = () => {
  hasScrolled.value = (window.scrollY || 0) > 6
}

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}

onMounted(() => {
  handleScroll()
  window.addEventListener('scroll', handleScroll, { passive: true })
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header
    class="fixed inset-x-0 top-0 z-50 border-b border-[var(--border)] bg-white transition-shadow duration-[400ms] ease-in-out"
    :class="hasScrolled ? 'shadow-[0_8px_24px_-20px_rgba(0,0,0,0.45)]' : 'shadow-none'"
  >
    <div class="site-container">
      <div class="flex h-[88px] items-center justify-between">
        <a
          href="#top"
          class="inline-flex items-center rounded-full px-1 py-1"
          @click="closeMenu"
        >
          <span
            class="font-display text-2xl leading-none tracking-[0.16em] text-[var(--text)] sm:text-3xl"
          >
            MONTE NERO
          </span>
        </a>

        <nav class="hidden items-center gap-8 md:flex">
          <a
            v-for="item in siteContent.navigation"
            :key="item.href"
            :href="item.href"
            class="text-sm font-medium text-[var(--text-muted)] transition-colors duration-[400ms] ease-in-out hover:text-[var(--text)]"
          >
            {{ item.label }}
          </a>
        </nav>

        <div class="hidden md:block">
          <a :href="siteContent.headerCta.href" class="btn-primary">
            {{ siteContent.headerCta.label }}
          </a>
        </div>

        <button
          type="button"
          class="inline-flex h-11 w-11 items-center justify-center rounded-full border border-[var(--border)] text-[var(--text)] transition-colors duration-[400ms] ease-in-out hover:bg-[var(--surface)] md:hidden"
          :aria-label="isMenuOpen ? 'Закрыть меню' : 'Открыть меню'"
          @click="toggleMenu"
        >
          <XMarkIcon v-if="isMenuOpen" class="h-6 w-6" />
          <Bars3Icon v-else class="h-6 w-6" />
        </button>
      </div>
    </div>

    <transition name="menu">
      <div
        v-if="isMenuOpen"
        class="border-t border-[var(--border)] bg-white px-6 py-4 md:hidden"
      >
        <nav class="mx-auto flex max-w-7xl flex-col gap-2">
          <a
            v-for="item in siteContent.navigation"
            :key="item.href"
            :href="item.href"
            class="rounded-xl px-4 py-3 text-sm font-medium text-[var(--text)] transition-colors duration-[400ms] ease-in-out hover:bg-[var(--surface)]"
            @click="closeMenu"
          >
            {{ item.label }}
          </a>
          <a
            :href="siteContent.headerCta.href"
            class="btn-primary mt-2 w-full"
            @click="closeMenu"
          >
            {{ siteContent.headerCta.label }}
          </a>
        </nav>
      </div>
    </transition>
  </header>
</template>
