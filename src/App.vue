<script setup>
import { onBeforeUnmount, onMounted } from 'vue'
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import SolutionsSection from './components/SolutionsSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import FaqSection from './components/FaqSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'

let observer

const REVEAL_TRANSITION_MS = 450

onMounted(() => {
  const scheduledReveal = new WeakSet()

  const revealElement = (element) => {
    if (!observer) {
      return
    }

    if (scheduledReveal.has(element)) {
      return
    }

    scheduledReveal.add(element)

    requestAnimationFrame(() => {
      requestAnimationFrame(() => {
        if (!observer) {
          return
        }

        element.classList.add('is-visible')
        observer.unobserve(element)

        const delayValue = Number(element.getAttribute('data-delay') || '0')
        const safeDelay = Number.isFinite(delayValue) ? Math.max(0, delayValue) : 0

        window.setTimeout(() => {
          element.style.setProperty('--reveal-delay', '0ms')
        }, safeDelay + REVEAL_TRANSITION_MS)
      })
    })
  }

  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (!entry.isIntersecting) {
          return
        }

        revealElement(entry.target)
      })
    },
    {
      threshold: 0.05,
      rootMargin: '0px 0px -6% 0px'
    }
  )

  const revealElements = document.querySelectorAll('[data-reveal]')
  revealElements.forEach((element) => {
    const animation = element.getAttribute('data-anim')
    if (animation) {
      element.classList.add(`reveal-${animation}`)
    } else {
      element.classList.add('reveal-up')
    }

    const delayValue = Number(element.getAttribute('data-delay') || '0')
    element.style.setProperty('--reveal-delay', `${Math.max(0, delayValue)}ms`)

    observer.observe(element)
  })
})

onBeforeUnmount(() => {
  if (observer) {
    observer.disconnect()
    observer = undefined
  }
})
</script>

<template>
  <div
    id="top"
    class="page-shell relative overflow-x-hidden bg-[var(--background)] text-[var(--text)]"
  >
    <div
      aria-hidden="true"
      class="pointer-events-none fixed inset-x-0 top-0 -z-10 h-[420px] bg-[radial-gradient(circle_at_15%_0%,rgba(26,26,26,0.08),transparent_55%),radial-gradient(circle_at_80%_0%,rgba(95,95,95,0.09),transparent_50%)]"
    />

    <AppHeader />

    <main class="pt-[88px]">
      <HeroSection />
      <SolutionsSection />
      <ServicesSection />
      <ProjectsSection />
      <FaqSection />
      <ContactSection />
    </main>

    <AppFooter />
  </div>
</template>
