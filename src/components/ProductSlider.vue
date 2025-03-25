<template>
  <div class="product-slider">
    <swiper-container ref="swiper" init="false">
      <swiper-slide v-for="(image, index) in images" :key="index">
        <v-img :src="image" class="product-slider__image" cover />
      </swiper-slide>
    </swiper-container>
    <div class="swiper-pagination"></div>
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { register } from 'swiper/element/bundle';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

defineProps({
  images: {
    type: Array,
    required: true,
  },
});

const swiper = ref(null);

onMounted(() => {
  register();
  const swiperEl = swiper.value;
  Object.assign(swiperEl, {
    loop: true,
    navigation: {
      nextEl: '.swiper-button-prev',
      prevEl: '.swiper-button-next',
    },
    pagination: {
      el: '.swiper-pagination',
      clickable: true,
    },
    autoplay: {
      delay: 3000,
      disableOnInteraction: false,
    },
  });
  swiperEl.initialize();
});
</script>

<style lang="scss" scoped>
.product-slider {
  position: relative;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);

  &__image {
    height: 400px;
    object-fit: cover;
    border-radius: 8px;
  }

  .swiper-button-prev,
  .swiper-button-next {
    color: #fff;
    background: rgba(0, 0, 0, 0.5);
    border-radius: 50%;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.3s;

    &:hover {
      background: rgba(0, 0, 0, 0.8);
    }

    &::after {
      font-size: 20px;
    }
  }

  .swiper-pagination {
    bottom: 10px !important;

    .swiper-pagination-bullet {
      background: #fff;
      opacity: 0.7;
      transition: opacity 0.3s;

      &.swiper-pagination-bullet-active {
        opacity: 1;
        background: #1976d2;
      }
    }
  }
}
</style>