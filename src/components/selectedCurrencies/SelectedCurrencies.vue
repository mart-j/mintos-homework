<template>
  <div class="currencies-wrapper">
    <div
      class="currency-wrapper"
      v-for="(currency, i) in selectedCurrencies"
      :key="i"
    >
      <div class="currency">
        <div class="currency__label">{{ currency.title }}</div>
        <button
          class="currency__remove-button"
          @click="$emit('selectHandler', currency)"
        >
          X
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { CurrencyType } from '../../data/currencies';

export default defineComponent({
  name: 'SelectedCurrencies',
  emits: ['selectHandler'],
  props: {
    CurrencyList: { type: Array as () => CurrencyType[], required: true },
  },
  computed: {
    selectedCurrencies(): CurrencyType[] {
      return this.CurrencyList.filter((currency) => currency.selected);
    },
  },
});
</script>

<style lang="scss" scoped>
@import './SelectedCurrencies.scss';
</style>
