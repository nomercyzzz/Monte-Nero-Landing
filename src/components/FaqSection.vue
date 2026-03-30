<template>
  <section id="faq" class="section-shell border-t border-[var(--border)]">
    <div class="site-container">
      <div class="max-w-3xl" data-reveal data-anim="left">
        <p
          class="text-xs font-semibold uppercase tracking-[0.2em] text-[var(--text-muted)]"
        >
          {{ siteContent.faq.kicker }}
        </p>
        <h2 class="font-display mt-4 text-3xl text-[var(--text)] sm:text-4xl">
          {{ siteContent.faq.title }}
        </h2>
        <p class="mt-5 text-base leading-relaxed text-[var(--text-muted)]">
          {{ siteContent.faq.description }}
        </p>
      </div>

      <div class="mt-10 space-y-3">
        <article
          v-for="(item, index) in siteContent.faq.items"
          :key="item.question"
          data-reveal
          data-anim="up"
          :data-delay="index * 45"
          class="rounded-2xl border border-[var(--border)] bg-[var(--surface)] px-5 py-4 shadow-fade-soft"
        >
          <button
            type="button"
            class="flex w-full items-center justify-between gap-4 text-left"
            @click="toggleItem(index)"
          >
            <span class="text-base font-semibold text-[var(--text)] sm:text-lg">
              {{ item.question }}
            </span>
            <span
              class="inline-flex h-8 w-8 items-center justify-center rounded-full border border-[var(--border)] bg-white text-[var(--text-muted)] transition-transform duration-[400ms] ease-in-out"
              :class="isOpen(index) ? 'rotate-0' : '-rotate-90'"
            >
              <ChevronDownIcon v-if="isOpen(index)" class="h-4 w-4" />
              <span v-else class="text-lg font-semibold leading-none">&gt;</span>
            </span>
          </button>

          <div
            class="grid overflow-hidden transition-all duration-[400ms] ease-in-out"
            :class=" isOpen(index)? 'grid-rows-[1fr] pt-4 opacity-100': 'grid-rows-[0fr] opacity-0'">
            <div class="min-h-0">
              <p class="text-sm leading-relaxed text-[var(--text-muted)]">
                {{ item.answer }}
              </p>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { ChevronDownIcon } from '@heroicons/vue/24/outline'
import siteContent from '../content/siteContent'

const openItems = ref(new Set([0]))

const isOpen = (index) => openItems.value.has(index)

const toggleItem = (index) => {
  const next = new Set(openItems.value)
  if (next.has(index)) {
    next.delete(index)
  } else {
    next.add(index)
  }
  openItems.value = next
}
</script>

