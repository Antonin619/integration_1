<template>
    <div v-if="props" class="credit_card shadow-lg">

        <div class="balance">
            <h3 class="balance-title">Balance</h3>
            <h4 class="amount">{{ amount }} €</h4>
        </div>

        <div class="card-info">
            <div class="names">
                <h2 class="firstname">{{ firstname }}</h2>
                <h2 class="lastname">{{ lastname }}</h2>
            </div>

            <div class="card-number-infos">
                <h5 class="card-number">{{ cardNumber }}</h5>
                <h5 class="card-date">{{ cardPeremptionDate }}</h5>
            </div>
        </div>
        
    </div>
</template>

<script lang="ts" setup>
import Chart from 'chart.js/auto';


const props = defineProps<{
    amount: number,
    firstname: string,
    lastname: string,
    cardNumber: number,
    cardPeremptionDate: string
}>()
</script>

<style lang="scss" scoped>


.credit_card {
    border-radius: 1rem;
    background-image: url('../assets/card_bg.png');
    background-size: cover;
    background-position: center;
    padding: 1rem;
    padding-left: 1.8rem;
    padding-right: 1.8rem;
    margin-top: 2rem;
    margin-bottom: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 5rem;
    
    .balance {

        .balance-title {
            font-weight: 600;
            font-size: 14px;
        }

        .amount {
            font-weight: 600;
            font-size: 32px;
            color: rgb(92, 92, 92);
        }
    }

    .card-info {

        .names {

            display: flex; gap: 0.5rem;

            .firstname {
                font-weight: 600;
                font-size: 24px;
            }

            .lastname {
                font-weight: 600;
                font-size: 24px;
                text-transform: uppercase;
            }
        }

        .card-number-infos {
            display: flex; gap: 1rem;
            align-items: center;
            justify-content: space-between;

            .card-number {
                font-weight: 600;
                font-size: 24px;
                color: grey;
            }

            .card-date {
                font-weight: 600;
                font-size: 14px;
                color: rgb(77, 77, 77);
            }
        }
    }
}
</style>