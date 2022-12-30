<template>
    <div v-if="props" class="currency_card shadow-lg" :style="`background-color: ${color}`">

        <div class="currency_card-content">
            <div class="currencies">
                <h5 class="currency-symbol">{{ currency }}</h5>
                <h4 class="currency-name">{{ currencyName }}</h4>
            </div>
            <h3 class="amount">{{ formattedAmount }}</h3>
      
            <p class="increase-text">{{ increase }}% increase in 30 days</p>

            <div class="options">
                <font-awesome-icon class="burger" icon="fa-solid fa-credit-card" />
                <font-awesome-icon class="burger" icon="fa-solid fa-circle-plus" />
            </div>
        </div>
        
    </div>
</template>

<script lang="ts" setup>

const props = defineProps<{
    currency: string,
    currencyName: string,
    amount: number,
    increase: string,
    color: string
}>()

function intToString (value:number) {
    var suffixes = ["", "k", "m", "b","t"];
    var suffixNum = Math.floor((""+value).length/4);
    var shortValue = parseFloat((suffixNum != 0 ? (value / Math.pow(1000,suffixNum)) : value).toPrecision(2));
    return shortValue+suffixes[suffixNum];
}

const formattedAmount = intToString(props.amount)
</script>

<style lang="scss" scoped>


.currency_card {
    margin-bottom: 6%;
    border-radius: 1rem;
    aspect-ratio: 1/1;
    
    .currency_card-content {
        padding: 1rem;

        .currencies {
            display: flex;
            align-items: end;
            gap: 4px;

            .currency-symbol {
                font-size: 2rem;
                font-weight: 600;
                color: black;
            }

            .currency-name {
                font-size: 0.8rem;
                font-weight: 400;
                padding-bottom: 0.5rem;
                opacity: 0.5;
            }
        }

        .amount {
            width: 100%;
            border-bottom: 1px solid rgba(0, 0, 0, 0.237);
            font-size: 1.8rem;
            font-weight: 600;
            margin-top: 0.7rem;
            padding-bottom: 0.5rem;
        }

        .increase-text {
            font-size: 10px;
            opacity: 0.5;
            padding-top: 0.3rem;
            padding-bottom: 0.3rem;
        }

        .options {
            display: flex;
            justify-content: space-between;
            font-size: 1.4rem;
            color: rgba(0, 0, 0, 0.255)
        }
    }
}
</style>