<template>
    <div class="dashboard p-8">
        <h1>Dashboard</h1>
        
        <h2>Your Stats</h2>
        <h5 class="mb-10">A bird eye view on your portfolio</h5>
        <div class="stats-cards">
            <StatsCard :cardId="1" title="Bitcoin" :percentage="73.2" color="#ecbf44" :amount="1203920.12" />
            <StatsCard :cardId="2" title="Ethereum" :percentage="34.1" color="#e64c6b" :amount="50023.32" />
            <StatsCard :cardId="3" title="USDT" :percentage="89.9" color="#5aca52" :amount="2002.90" />
        </div>
        <div class="balance-ard">
            <BalanceCard :cardId="1" title="Current" :amount="1207830.12" />
        </div>

        <button class="explore-more shadow-md mb-24">
            + Explore More
        </button>

        <h2>Cards & Balance</h2>
        <h5>Your balances are looking good</h5>
        

        <CreditCard :amount="1398239" firstname="Antonin" lastname="Bourain" :cardNumber="490243905230330" cardPeremptionDate="12/2025"/>

        <div class="currency-box">
            <CurrencyCard v-for="card in currencyCards" :currency="card.currency" :currencyName="card.currencyName" :amount="card.amount" :increase="card.increase" :color="card.color"/>
        </div>

        <button class="explore-more shadow-md mb-24">
            + Explore More
        </button>
    </div>
</template>

<script lang="ts" setup>
import CreditCard from '~~/components/CreditCard.vue';
import CurrencyCard from '~~/components/CurrencyCard.vue';

const currencyCards = ref([
    {
        currency: "€",
        currencyName: "Euro",
        amount: 1207830.12,
        increase: '13.2',
        color: '#FADEB8'
    },
    {
        currency: "$",
        currencyName: "USDT",
        amount: 77740730.12,
        increase: '24',
        color: '#FECDC9'
    },
    {
        currency: "£",
        currencyName: "Pound",
        amount: 0.00,
        increase: '0',
        color: '#E7E3E2'
    },
    {
        currency: "¥",
        currencyName: "Yen",
        amount: 1239,
        increase: '33.2',
        color: '#C5DCE5'
    }
])

</script>

<style lang="scss" scoped>
    .explore-more {
        background-color: white;
        color: rgb(71, 0, 185);
        border: none;
        border-radius: 2rem;
        padding: 1rem 2rem 1rem 2rem;
        margin-top: 2rem;
        font-size: 1.2rem;
        font-weight: 700;
        width: 100%;
        cursor: pointer;
        box-shadow: 0 0px 10px 5px rgba(0, 0, 0, 0.1);
    }

    .currency-box {
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        gap: 6%;
      }
      .currency-box>* {
          flex: 0 0 47%;
      }
</style>