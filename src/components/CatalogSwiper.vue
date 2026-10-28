<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Navigation, Pagination } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'

import catalog1 from '@/assets/catalogo/WhatsApp Image 2026-10-27 at 10.49.30 AM.jpeg'
import catalog2 from '@/assets/catalogo/WhatsApp Image 2026-10-27 at 10.49.31 AM.jpeg'
import catalog3 from '@/assets/catalogo/WhatsApp Image 2026-10-27 at 10.49.31 AM (1).jpeg'
import catalog4 from '@/assets/catalogo/WhatsApp Image 2026-10-27 at 10.49.31 AM (2).jpeg'
import catalog5 from '@/assets/catalogo/WhatsApp Image 2026-10-27 at 10.49.31 AM (3).jpeg'

const modules = [Autoplay, Navigation, Pagination]
const catalogs = [
  { src: catalog1 },
  { src: catalog2 },
  { src: catalog3 },
  { src: catalog4 },
  { src: catalog5 },
]
</script>

<template>
  <section class="catalog-section" aria-labelledby="catalog-title">
    <div class="catalog-heading">
      <p class="catalog-kicker">Novos produtos</p>
      <h2 id="catalog-title">Catálogo da semana</h2>
      <div class="offer-badge" aria-label="Oferta do dia">
        <span>Oferta do dia</span>
      </div>
    </div>

    <Swiper
      class="catalog-swiper"
      :modules="modules"
      :slides-per-view="1"
      :space-between="18"
      :loop="true"
      :autoplay="{ delay: 3500, disableOnInteraction: false }"
      :pagination="{ clickable: true }"
      :navigation="true"
      :breakpoints="{
        640: { slidesPerView: 2 },
        980: { slidesPerView: 3 }
      }"
    >
      <SwiperSlide v-for="(catalog, index) in catalogs" :key="catalog.src">
        <article class="catalog-card">
          <img :src="catalog.src" :alt="`Catálogo de produtos ${index + 1}`" loading="lazy" />
        </article>
      </SwiperSlide>
    </Swiper>
  </section>
</template>



<style scoped>
.catalog-section {
  padding: 5rem 7%;
  overflow: hidden;
  background: var(--off-white);
}

.catalog-heading {
  position: relative;
  margin-bottom: 2rem;
  text-align: center;
}

.catalog-kicker {
  margin-bottom: 0.35rem;
  color: var(--blue);
  font-size: 0.72rem;
  font-weight: 800;
  letter-spacing: 2.5px;
  text-transform: uppercase;
}

.catalog-heading h2 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(1.8rem, 3vw, 2.8rem);
  color: var(--black);
}

.offer-badge {
  width: fit-content;
  margin: 1rem auto 0;
  padding: 0.55rem 1.25rem;
  border-radius: 999px;
  background: var(--lime);
  box-shadow: 0 0 0 0 rgba(204, 238, 0, 0.65);
  animation: offerPulse 1.8s infinite;
}

.offer-badge span {
  color: var(--black);
  font-weight: 900;
  letter-spacing: 1px;
  text-transform: uppercase;
}

.catalog-swiper {
  padding-bottom: 3.5rem;
}

.catalog-card {
  height: 520px;
  overflow: hidden;
  border-radius: 12px;
  background: var(--white);
  box-shadow: 0 14px 35px rgba(18, 29, 25, 0.12);
}

.catalog-card img {
  width: 100%;
  height: 100%;
  display: block;
  object-fit: cover;
}

.catalog-swiper :deep(.swiper-button-prev),
.catalog-swiper :deep(.swiper-button-next) {
  width: 42px;
  height: 42px;
  border-radius: 50%;
  background: var(--white);
  color: var(--blue);
  box-shadow: 0 5px 18px rgba(18, 29, 25, 0.18);
}

.catalog-swiper :deep(.swiper-button-prev::after),
.catalog-swiper :deep(.swiper-button-next::after) {
  font-size: 17px;
  font-weight: 900;
}

.catalog-swiper :deep(.swiper-pagination-bullet-active) {
  background: var(--blue);
}

@keyframes offerPulse {
  0%, 100% { transform: scale(1) rotate(-1deg); box-shadow: 0 0 0 0 rgba(204, 238, 0, 0.65); }
  50% { transform: scale(1.06) rotate(1deg); box-shadow: 0 0 0 12px rgba(204, 238, 0, 0); }
}

@media (prefers-reduced-motion: reduce) {
  .offer-badge { animation: none; }
}

@media (max-width: 640px) {
  .catalog-section { padding: 4rem 5%; }
  .catalog-card { height: 430px; }
}
</style>
