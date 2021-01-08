<template>
  <div class="container">
    <SelectedCurrencies
      @selectHandler="selectCurrency"
      :CurrencyList="CurrencyList"
    />
    <Currencies @selectHandler="selectCurrency" :CurrencyList="CurrencyList" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Currencies from './components/currencies/Currencies.vue';
import SelectedCurrencies from './components/selectedCurrencies/SelectedCurrencies.vue';
import CurrencyList, { CurrencyType } from './data/currencies';

export default defineComponent({
  name: 'App',
  components: {
    Currencies,
    SelectedCurrencies,
  },

  data() {
    return {
      value: '',
      CurrencyList,
    };
  },
  methods: {
    selectCurrency(currency: CurrencyType) {
      const currencyIndex = this.CurrencyList.indexOf(currency);
      const selectedCurrency = this.CurrencyList[currencyIndex];
      selectedCurrency.selected = !selectedCurrency.selected;
    },
  },
});
</script>

<style lang="scss">
@import './App.scss';
</style>
