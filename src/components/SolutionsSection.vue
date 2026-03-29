<template>
  <section id="solutions" class="section-shell border-t border-[var(--border)]">
    <div class="site-container">
      <div class="max-w-3xl" data-reveal data-anim="left">
        <p
          class="text-xs font-semibold uppercase tracking-[0.2em] text-[var(--text-muted)]"
        >
          {{ siteContent.solutions.kicker }}
        </p>
        <h2 class="font-display mt-4 text-3xl text-[var(--text)] sm:text-4xl">
          {{ siteContent.solutions.title }}
        </h2>
        <p class="mt-5 text-base leading-relaxed text-[var(--text-muted)]">
          {{ siteContent.solutions.description }}
        </p>
      </div>

      <div class="mt-12 grid gap-5 md:grid-cols-2 xl:grid-cols-3">
        <article
          v-for="(item, index) in siteContent.solutions.products"
          :key="item.title"
          data-reveal
          data-anim="up"
          :data-delay="index * 60"
          class="surface-card card-hover shadow-fade-soft p-5"
        >
          <Squares2X2Icon class="h-6 w-6 text-[var(--text-muted)]" />
          <h3 class="mt-4 text-lg font-semibold text-[var(--text)]">
            {{ item.title }}
          </h3>
          <p class="mt-2 text-sm leading-relaxed text-[var(--text-muted)]">
            {{ item.text }}
          </p>
        </article>
      </div>

      <div class="mt-8 grid gap-5 lg:grid-cols-2">
        <article data-reveal data-anim="up" class="surface-card shadow-fade-soft p-6">
          <div class="flex items-center gap-3">
            <CubeTransparentIcon class="h-6 w-6 text-[var(--text-muted)]" />
            <h3 class="text-xl font-semibold text-[var(--text)]">Материалы</h3>
          </div>
          <ul class="mt-5 space-y-4">
            <li
              v-for="material in siteContent.solutions.materials"
              :key="material.name"
              class="border-b border-[var(--border)] pb-4 last:border-none last:pb-0"
            >
              <p class="text-sm font-semibold uppercase tracking-[0.14em] text-[var(--text)]">
                {{ material.name }}
              </p>
              <p class="mt-1 text-sm leading-relaxed text-[var(--text-muted)]">
                {{ material.text }}
              </p>
            </li>
          </ul>
        </article>

        <article
          data-reveal
          data-anim="up"
          data-delay="80"
          class="surface-card shadow-fade-strong p-6"
        >
          <div class="flex items-center gap-3">
            <CheckBadgeIcon class="h-6 w-6 text-[var(--text-muted)]" />
            <h3 class="text-xl font-semibold text-[var(--text)]">Преимущества</h3>
          </div>
          <ul class="mt-5 space-y-3">
            <li
              v-for="advantage in siteContent.solutions.advantages"
              :key="advantage"
              class="flex items-start gap-3 rounded-xl border border-[var(--border)] bg-[var(--surface-soft)] px-4 py-3 text-sm text-[var(--text)]"
            >
              <span class="mt-[5px] inline-block h-1.5 w-1.5 rounded-full bg-[var(--accent)]" />
              <span class="leading-relaxed">{{ advantage }}</span>
            </li>
          </ul>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import {
  CheckBadgeIcon,
  CubeTransparentIcon,
  Squares2X2Icon
} from '@heroicons/vue/24/outline'
import siteContent from '../content/siteContent'
</script>


