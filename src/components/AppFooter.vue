<script setup>
import siteContent from '../content/siteContent'
import logoMark from '../assets/logos/monte-nero.svg'

</script>

<template>
  <footer class="border-t border-[#2b2b2b] bg-[#111111] py-12 text-white">
    <div class="site-container">
      <div class="grid gap-8 md:grid-cols-[1.2fr_1fr_1fr]">
        <div data-reveal data-anim="up">
          <p class="font-display text-3xl leading-none tracking-[0.18em]">MONTE NERO</p>
          <p class="mt-4 max-w-md text-sm leading-relaxed text-[#b8b8b8]">
            {{ siteContent.footer.description }}
          </p>
        </div>

        <div data-reveal data-anim="up" data-delay="70">
          <p class="text-xs uppercase tracking-[0.2em] text-[#8a8a8a]">Навигация</p>
          <nav class="mt-4 flex flex-col gap-2">
            <a
              v-for="item in siteContent.navigation"
              :key="item.href"
              :href="item.href"
              class="text-sm text-white/90 transition-colors duration-[400ms] ease-in-out hover:text-white"
            >
              {{ item.label }}
            </a>
          </nav>
        </div>

        <div data-reveal data-anim="up" data-delay="120">
          <p class="text-xs uppercase tracking-[0.2em] text-[#8a8a8a]">Контакты</p>
          <div class="mt-4 space-y-2 text-sm text-white/90">
            <a
              href="tel:+74950000000"
              class="block transition-opacity duration-[400ms] ease-in-out hover:opacity-70"
            >
              +7 (495) 000-00-00
            </a>
            <a
              href="https://t.me/montenero_stone"
              target="_blank"
              rel="noreferrer"
              class="block transition-opacity duration-[400ms] ease-in-out hover:opacity-70"
            >
              @montenero_stone
            </a>
            <a
              href="mailto:info@montenero.ru"
              class="block transition-opacity duration-[400ms] ease-in-out hover:opacity-70"
            >
              info@montenero.ru
            </a>
            <p>Москва, ул. Большая Никитская, 21</p>
          </div>
        </div>
      </div>

      <div
        class="mt-10 flex flex-col gap-4 border-t border-[#2b2b2b] pt-6 sm:flex-row sm:items-center sm:justify-between"
      >
        <a href="#top" class="inline-flex items-center gap-3">
          <img
            :src="logoMark"
            alt="Логотип MONTE NERO"
            class="h-9 w-9 brightness-0 invert"
            loading="lazy"
          />
          <span class="font-display text-xl tracking-[0.16em] text-white">MONTE NERO</span>
        </a>
        <p class="text-xs text-[#8a8a8a]">@ 2026 MONTE NERO. Все права защищены.</p>
      </div>
    </div>
  </footer>
</template>
