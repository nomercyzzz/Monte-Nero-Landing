<template>
  <section class="section-shell pt-14 md:pt-20">
    <div class="site-container">
      <div class="grid items-center gap-12 lg:grid-cols-[1.05fr_0.95fr] lg:gap-14">
        <div data-reveal data-anim="left">
          <p
            class="mb-4 inline-flex rounded-full border border-[var(--border)] bg-[var(--surface)] px-4 py-2 text-xs font-semibold uppercase tracking-[0.2em] text-[var(--text-muted)]"
          >
            {{ siteContent.hero.kicker }}
          </p>
          <h1
            class="font-display max-w-2xl text-4xl leading-tight text-[var(--text)] sm:text-5xl xl:text-6xl"
          >
            {{ siteContent.hero.title }}
          </h1>
          <p
            class="mt-6 max-w-xl text-base leading-relaxed text-[var(--text-muted)] sm:text-lg"
          >
            {{ siteContent.hero.description }}
          </p>
          <div class="mt-8 flex flex-wrap gap-3">
            <a :href="siteContent.hero.primaryCta.href" class="btn-primary">
              {{ siteContent.hero.primaryCta.label }}
            </a>
            <a :href="siteContent.hero.secondaryCta.href" class="btn-secondary">
              {{ siteContent.hero.secondaryCta.label }}
            </a>
          </div>
        </div>

        <div data-reveal data-anim="zoom" data-delay="90" class="group relative">
          <div class="surface-card overflow-hidden p-4 sm:p-5">
            <img
              :src="siteContent.hero.visual.image"
              :alt="siteContent.hero.visual.alt"
              class="image-zoom h-[340px] w-full rounded-xl object-cover sm:h-[420px]"
              loading="eager"
            />
          </div>

          <div
            class="surface-card-soft absolute -left-5 bottom-5 hidden max-w-[260px] p-4 md:block"
          >
            <p class="text-xs uppercase tracking-[0.2em] text-[var(--text-muted)]">
              MONTE NERO
            </p>
            <p class="mt-2 text-sm font-medium leading-relaxed text-[var(--text)]">
              Изделия из камня под проект: точно по размерам и в логике пространства.
            </p>
          </div>
        </div>
      </div>

      <ul class="mt-12 grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
        <li
          v-for="(point, index) in siteContent.hero.trustPoints"
          :key="point.title"
          data-reveal
          data-anim="up"
          :data-delay="index * 70"
          class="surface-card card-hover shadow-fade-soft p-5"
        >
          <p class="text-sm font-semibold uppercase tracking-[0.16em] text-[var(--text)]">
            {{ point.title }}
          </p>
          <p class="mt-2 text-sm leading-relaxed text-[var(--text-muted)]">
            {{ point.text }}
          </p>
        </li>
      </ul>
    </div>
  </section>
</template>

<script setup>
import siteContent from '../content/siteContent'
</script>
