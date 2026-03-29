
<template>
  <section id="contacts" class="section-shell border-t border-[var(--border)]">
    <div class="site-container">
      <div class="grid gap-8 lg:grid-cols-[1.02fr_0.98fr]">
        <div
          data-reveal
          data-anim="left"
          class="rounded-3xl border border-[var(--border)] bg-[var(--surface)] p-6 shadow-fade-strong sm:p-8"
        >
          <p
            class="text-xs font-semibold uppercase tracking-[0.2em] text-[var(--text-muted)]"
          >
            {{ siteContent.contacts.kicker }}
          </p>
          <h2 class="font-display mt-4 text-3xl text-[var(--text)] sm:text-4xl">
            {{ siteContent.contacts.title }}
          </h2>
          <p class="mt-5 text-base leading-relaxed text-[var(--text-muted)]">
            {{ siteContent.contacts.description }}
          </p>

          <div class="mt-8 space-y-3">
            <div
              v-for="(item, index) in siteContent.contacts.details"
              :key="item.label"
              data-reveal
              data-anim="up"
              :data-delay="index * 40"
              class="flex items-start gap-3 rounded-2xl border border-[var(--border)] bg-white px-4 py-3 shadow-fade-soft"
            >
              <component
                :is="getContactIcon(item.label)"
                class="mt-[2px] h-5 w-5 text-[var(--text-muted)]"
              />
              <div>
                <p class="text-xs uppercase tracking-[0.16em] text-[var(--text-muted)]">
                  {{ item.label }}
                </p>
                <a
                  v-if="item.href"
                  :href="item.href"
                  target="_blank"
                  rel="noreferrer"
                  class="mt-1 inline-block text-sm font-medium text-[var(--text)] transition-opacity duration-[400ms] ease-in-out hover:opacity-70"
                >
                  {{ item.value }}
                </a>
                <p v-else class="mt-1 text-sm font-medium text-[var(--text)]">
                  {{ item.value }}
                </p>
              </div>
            </div>
          </div>
        </div>

        <div
          data-reveal
          data-anim="up"
          data-delay="90"
          class="rounded-3xl border border-[var(--border)] bg-white p-6 shadow-fade-strong sm:p-8"
        >
          <h3 class="text-2xl font-semibold text-[var(--text)]">Форма заявки</h3>
          <p class="mt-2 text-sm leading-relaxed text-[var(--text-muted)]">
            Заполните форму, чтобы получить расчет проекта и подобрать материал.
          </p>

          <form class="mt-6 space-y-4" @submit.prevent="submitForm">
            <label class="block">
              <span class="mb-2 block text-sm font-medium text-[var(--text)]">
                {{ siteContent.contacts.form.nameLabel }}
              </span>
              <input
                v-model="form.name"
                type="text"
                required
                class="w-full rounded-xl border border-[var(--border)] bg-[var(--surface)] px-4 py-3 text-sm outline-none transition-colors duration-[400ms] ease-in-out focus:border-[var(--accent)]"
                placeholder="Ваше имя"
              />
            </label>

            <label class="block">
              <span class="mb-2 block text-sm font-medium text-[var(--text)]">
                {{ siteContent.contacts.form.phoneLabel }}
              </span>
              <input
                v-model="form.phone"
                type="tel"
                required
                class="w-full rounded-xl border border-[var(--border)] bg-[var(--surface)] px-4 py-3 text-sm outline-none transition-colors duration-[400ms] ease-in-out focus:border-[var(--accent)]"
                placeholder="+7 (___) ___-__-__"
              />
            </label>

            <label class="block">
              <span class="mb-2 block text-sm font-medium text-[var(--text)]">
                {{ siteContent.contacts.form.messageLabel }}
              </span>
              <textarea
                v-model="form.message"
                rows="4"
                class="w-full resize-none rounded-xl border border-[var(--border)] bg-[var(--surface)] px-4 py-3 text-sm outline-none transition-colors duration-[400ms] ease-in-out focus:border-[var(--accent)]"
                placeholder="Например: кухня, столешница, стеновая панель, сроки проекта"
              />
            </label>

            <button type="submit" class="btn-primary w-full">
              {{ siteContent.contacts.form.submitLabel }}
            </button>
          </form>

          <p class="mt-4 text-xs leading-relaxed text-[var(--text-muted)]">
            {{ siteContent.contacts.form.note }}
          </p>

          <p
            v-if="isSubmitted"
            class="mt-4 rounded-xl border border-[var(--border)] bg-[var(--surface)] px-4 py-3 text-sm text-[var(--text)]"
          >
            Спасибо. Заявка принята в обработку. Мы свяжемся с вами для обсуждения задачи.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue'
import {
  ClockIcon,
  EnvelopeIcon,
  MapPinIcon,
  PaperAirplaneIcon,
  PhoneIcon
} from '@heroicons/vue/24/outline'
import siteContent from '../content/siteContent'

const form = reactive({
  name: '',
  phone: '',
  message: ''
})

const isSubmitted = ref(false)

const submitForm = () => {
  isSubmitted.value = true
  form.name = ''
  form.phone = ''
  form.message = ''
}

const getContactIcon = (label) => {
  const normalized = String(label || '').toLowerCase()

  if (normalized.includes('telegram')) {
    return PaperAirplaneIcon
  }

  if (normalized.includes('тел')) {
    return PhoneIcon
  }

  if (normalized.includes('email') || normalized.includes('mail')) {
    return EnvelopeIcon
  }

  if (normalized.includes('адрес') || normalized.includes('address')) {
    return MapPinIcon
  }

  if (normalized.includes('часы') || normalized.includes('hours')) {
    return ClockIcon
  }

  return PhoneIcon
}
</script>
