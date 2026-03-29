<template>
  <section id="services" class="section-shell border-t border-[var(--border)]">
    <div class="site-container">
      <div class="max-w-3xl" data-reveal data-anim="left">
        <p
          class="text-xs font-semibold uppercase tracking-[0.2em] text-[var(--text-muted)]"
        >
          {{ siteContent.services.kicker }}
        </p>
        <h2 class="font-display mt-4 text-3xl text-[var(--text)] sm:text-4xl">
          {{ siteContent.services.title }}
        </h2>
        <p class="mt-5 text-base leading-relaxed text-[var(--text-muted)]">
          {{ siteContent.services.description }}
        </p>
      </div>

      <div class="mt-12 grid gap-5 md:grid-cols-2 xl:grid-cols-3">
        <article
          v-for="(item, index) in siteContent.services.items"
          :key="item.title"
          data-reveal
          data-anim="up"
          :data-delay="index * 55"
          class="surface-card card-hover shadow-fade-soft p-5"
        >
          <component
            :is="serviceIcons[index % serviceIcons.length]"
            class="h-6 w-6 text-[var(--text-muted)]"
          />
          <h3 class="mt-4 text-lg font-semibold text-[var(--text)]">
            {{ item.title }}
          </h3>
          <p class="mt-2 text-sm leading-relaxed text-[var(--text-muted)]">
            {{ item.text }}
          </p>
        </article>
      </div>

      <div class="mt-10 rounded-3xl border border-[var(--border)] bg-[var(--surface)] p-6 sm:p-8">
        <div class="flex items-center justify-between gap-4" data-reveal data-anim="up">
          <h3 class="text-xl font-semibold text-[var(--text)]">Этапы работы</h3>
          <p class="text-sm text-[var(--text-muted)]">От заявки до установки</p>
        </div>

        <div class="mt-6 grid gap-4 lg:grid-cols-4">
          <article
            v-for="(stage, index) in siteContent.services.stages"
            :key="stage.label"
            data-reveal
            data-anim="up"
            :data-delay="index * 70"
            class="rounded-2xl border border-[var(--border)] bg-white p-4 shadow-fade-soft"
          >
            <p class="text-xs font-semibold uppercase tracking-[0.2em] text-[var(--text-muted)]">
              {{ stage.label }}
            </p>
            <h4 class="mt-3 text-base font-semibold text-[var(--text)]">
              {{ stage.title }}
            </h4>
            <p class="mt-2 text-sm leading-relaxed text-[var(--text-muted)]">
              {{ stage.text }}
            </p>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {
  ChatBubbleBottomCenterTextIcon,
  Cog6ToothIcon,
  PencilSquareIcon,
  SwatchIcon,
  TruckIcon,
  WrenchScrewdriverIcon
} from '@heroicons/vue/24/outline'
import siteContent from '../content/siteContent'

const serviceIcons = [
  ChatBubbleBottomCenterTextIcon,
  SwatchIcon,
  PencilSquareIcon,
  Cog6ToothIcon,
  TruckIcon,
  WrenchScrewdriverIcon
]
</script>

