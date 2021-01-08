<template>
  <div class="currencies-wrapper">
    <div
      class="currency-wrapper"
      v-for="(currency, i) in CurrencyList"
      :key="i"
    >
      <button
        :class="{ currency: true, ['currency--selected']: currency.selected }"
        @click="$emit('selectHandler', currency)"
      >
        <div class="checkbox-wrapper">
          <input class="checkbox" v-model="currency.selected" type="checkbox" />
          <div class="checkmark"><b>X</b></div>
        </div>

        <span class="currency-label">
          {{ currency.title }}
        </span>
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { CurrencyType } from '@/data/currencies';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Currencies',
  emits: ['selectHandler'],
  props: {
    CurrencyList: { type: Array as () => CurrencyType[], required: true },
  },
});
</script>

<style lang="scss" scoped>
@import './Currencies.scss';
</style>
