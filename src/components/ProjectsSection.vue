<template>
  <section id="projects" class="section-shell border-t border-[var(--border)]">
    <div class="site-container">
      <div class="max-w-3xl" data-reveal data-anim="left">
        <p
          class="text-xs font-semibold uppercase tracking-[0.2em] text-[var(--text-muted)]"
        >
          {{ siteContent.projects.kicker }}
        </p>
        <h2 class="font-display mt-4 text-3xl text-[var(--text)] sm:text-4xl">
          {{ siteContent.projects.title }}
        </h2>
        <p class="mt-5 text-base leading-relaxed text-[var(--text-muted)]">
          {{ siteContent.projects.description }}
        </p>
      </div>

      <div class="mt-12 grid gap-6 lg:grid-cols-3">
        <article
          v-for="(project, index) in siteContent.projects.featured"
          :key="project.title"
          data-reveal
          data-anim="up"
          :data-delay="index * 75"
          class="group surface-card card-hover shadow-fade-strong overflow-hidden p-4"
        >
          <div class="overflow-hidden rounded-xl border border-[var(--border)]">
            <img
              :src="project.image"
              :alt="project.title"
              class="image-zoom h-56 w-full object-cover"
              loading="lazy"
            />
          </div>
          <div class="mt-4">
            <div class="flex items-start justify-between gap-3">
              <p class="text-lg font-semibold text-[var(--text)]">
                {{ project.title }}
              </p>
              <span
                class="rounded-full border border-[var(--border)] bg-white px-3 py-1 text-xs font-medium text-[var(--text-muted)]"
              >
                {{ project.type }}
              </span>
            </div>

            <p class="mt-3 text-sm leading-relaxed text-[var(--text-muted)]">
              {{ project.text }}
            </p>

            <ul class="mt-4 space-y-2 text-sm text-[var(--text)]">
              <li class="flex items-center justify-between gap-2">
                <span class="text-[var(--text-muted)]">Материал</span>
                <span class="font-medium">{{ project.material }}</span>
              </li>
              <li class="flex items-center justify-between gap-2">
                <span class="text-[var(--text-muted)]">Формат</span>
                <span class="text-right font-medium">{{ project.scope }}</span>
              </li>
            </ul>

            <span
              class="mt-5 inline-flex items-center gap-1 text-sm font-medium text-[var(--text)]"
            >
              Подробнее по задаче
              <ArrowUpRightIcon class="h-4 w-4" />
            </span>
          </div>
        </article>
      </div>

      <div class="mt-12" data-reveal data-anim="soft">
        <div class="mb-5 flex items-center justify-between gap-4">
          <h3 class="text-xl font-semibold text-[var(--text)]">Мини-галерея</h3>
          <p class="text-sm text-[var(--text-muted)]">6 референсных фрагментов</p>
        </div>
        <div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
          <article
            v-for="(item, index) in siteContent.projects.gallery"
            :key="item.title"
            data-reveal
            data-anim="up"
            :data-delay="index * 50"
            class="group overflow-hidden rounded-2xl border border-[var(--border)] bg-[var(--surface)] p-3 shadow-fade-soft"
          >
            <div class="overflow-hidden rounded-xl border border-[var(--border)]">
              <img
                :src="item.image"
                :alt="item.title"
                class="image-zoom h-40 w-full object-cover"
                loading="lazy"
              />
            </div>
            <div class="mt-3 flex items-center justify-between gap-3">
              <p class="text-sm font-medium text-[var(--text)]">
                {{ item.title }}
              </p>
              <span class="text-xs uppercase tracking-[0.14em] text-[var(--text-muted)]">
                {{ item.tag }}
              </span>
            </div>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ArrowUpRightIcon } from '@heroicons/vue/24/outline'
import siteContent from '../content/siteContent'
</script>

