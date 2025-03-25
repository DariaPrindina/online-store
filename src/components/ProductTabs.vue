<template>
  <div class="product-tabs-wrapper">
    <v-tabs v-model="activeTab" class="product-tabs" color="primary">
      <v-tab>Описание</v-tab>
      <v-tab>Характеристики</v-tab>

      <v-tab-item>
        <v-card flat class="product-tabs__content">
          <v-card-text>{{ description }}</v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>
        <v-card flat class="product-tabs__content">
          <v-card-text>
            <v-table>
              <tbody>
                <tr v-for="(spec, index) in specs" :key="index">
                  <td class="product-tabs__spec-key">{{ spec.key }}</td>
                  <td>{{ spec.value }}</td>
                </tr>
              </tbody>
            </v-table>
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs>
  </div>
</template>

<script setup>
import { ref } from 'vue';

defineProps({
  description: String,
  specs: Array,
});

const activeTab = ref(0);
</script>

<style lang="scss" scoped>
.product-tabs-wrapper {
  margin-top: 20px;
}

.product-tabs {
  border-bottom: 1px solid #e0e0e0;

  :deep(.v-tab) {
    text-transform: none;
    font-weight: 500;
    letter-spacing: 0;
  }

  :deep(.v-tabs-items) {
    position: relative !important;
    margin-top: 20px;
    width: 100%;
  }

  :deep(.v-window-item) {
    position: relative !important;
  }

  &__content {
    padding: 20px;
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
  }

  &__spec-key {
    font-weight: 600;
    color: #424242;
  }
}
</style>