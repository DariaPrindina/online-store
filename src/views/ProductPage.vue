<template>
  <v-container class="product-page">
    <v-row>
      <v-col cols="12" md="6">
        <product-slider :images="product.images" />
      </v-col>
      <v-col cols="12" md="6">
        <v-row>
          <v-col cols="12">
            <h1 class="product-page__title">{{ product.name }}</h1>
            <p class="product-page__price">{{ product.price }} ₽</p>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <product-tabs :description="product.description" :specs="product.specs" />
          </v-col>
        </v-row>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" md="6" offset-md="6">
        <order-form />
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import ProductSlider from '@/components/ProductSlider.vue';
import ProductTabs from '@/components/ProductTabs.vue';
import OrderForm from '@/components/OrderForm.vue';

const product = {
  name: 'Смартфон Example Pro',
  price: 59990,
  images: [
    'https://images.unsplash.com/photo-1601784551446-20c9e07cdbdb?q=80&w=800&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1598327105666-5b89351aff97?q=80&w=800&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1600585154340-be6161a56a0c?q=80&w=800&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1610945415295-d9bbf067e59c?q=80&w=800&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1592890288564-76628a30a657?q=80&w=800&auto=format&fit=crop',
  ],
  description: 'Современный смартфон с мощным процессором и отличной камерой. Поддерживает 5G, имеет яркий AMOLED-дисплей и мощную батарею на 5000 мАч.',
  specs: [
    { key: 'Процессор', value: '8 ядер, 2.8 ГГц' },
    { key: 'Память', value: '128 ГБ' },
    { key: 'Экран', value: '6.5" AMOLED' },
    { key: 'Камера', value: '48 МП + 12 МП' },
    { key: 'Батарея', value: '5000 мАч' },
  ],
};
</script>

<style lang="scss" src="@/assets/styles/product.scss"></style>