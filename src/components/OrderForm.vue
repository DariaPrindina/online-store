<template>
  <v-form ref="form" v-model="valid" class="order-form" @submit.prevent="submit">
    <v-text-field
      v-model="name"
      label="Ваше имя"
      :rules="[v => !!v || 'Введите имя']"
      outlined
      dense
      prepend-inner-icon="mdi-account"
    />
    <v-text-field
      v-model="phone"
      label="Телефон"
      :rules="[v => !!v || 'Введите телефон']"
      outlined
      dense
      prepend-inner-icon="mdi-phone"
    />
    <v-btn type="submit" color="primary" :disabled="!valid" block class="order-form__button">
      Заказать сейчас
    </v-btn>
  </v-form>
</template>

<script setup>
import { ref } from 'vue';

const form = ref(null);
const valid = ref(false);
const name = ref('');
const phone = ref('');

const submit = () => {
  if (form.value.validate()) {
    alert('Заказ отправлен!');
  }
};
</script>

<style lang="scss" scoped>
@use 'sass:color';

.order-form {
  max-width: 400px;
  margin-top: 0;
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);

  &__button {
    margin-top: 10px;
    text-transform: none;
    font-weight: 500;
    padding: 10px 0;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    transition: background-color 0.3s;

    &:hover {
      background-color: color.adjust(#1976d2, $lightness: -10%);
    }
  }
}
</style>