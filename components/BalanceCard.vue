<template>
    <div v-if="props" class="balance_card">

        
        <div class="upper-side">
            <div class="balance-container flex"><h3 class="balance">{{ title }} Balance </h3><p class="percentage ml-2" :style="`color: green`">+{{ benefit }} %</p></div>
            <h4 class="amount">{{ amount }} €</h4>
        </div>
        <div class="bottom-side">
            
            <canvas :id="`myGraph${cardId}`"></canvas>
        </div>
        
    </div>
</template>

<script lang="ts" setup>
import Chart from 'chart.js/auto';

const props = defineProps<{
    cardId: number,
    title: string,
    amount: number
}>()

const labels = [ 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']
const data = {
  labels: labels,
  datasets: [{
    label: 'Balance (€)',
    data: [12, 23, 34, 36, 33, 55, 76, 65, 54, 43, 32, 43, 54, 32, 53, 67, 78],
    fill: true,
    borderColor: 'green',
    tension: 0.1,
  }]
};

const dataLength = data.datasets[0].data.length
const benefit = (data.datasets[0].data[dataLength-1]*100)/data.datasets[0].data[0]


new Chart(`myGraph${props.cardId}`, {
  type: 'line',
  data: data,
});



</script>

<style lang="scss" scoped>


.balance_card {
    backdrop-filter: blur(3px);
    border-radius: 2rem;
    box-shadow: 0 0px 10px 5px rgba(0, 0, 0, 0.1);
    padding: 2rem 1rem 2rem 1rem;
    display: flex;
    flex-direction: column;
    gap: 10px;

    .bottom-side {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        .percentage {
            font-size: 1.2rem;
            font-weight: 700;
            font-family: 'Poppins';
        }
    }

    .upper-side {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: start ;
        text-align: start;

        .balance-container {
            .balance {
                font-size: 1.2rem;
                font-weight: 600;
                font-family: 'Poppins';
                color: rgb(143, 143, 143);
            }

            p {
                font-weight: 600;
            }
        }

        .amount {
            font-size: 2.8rem;
            font-weight: 900;
            font-family: 'Poppins';
        }
        .card-button {
            border: none;
            background-color: transparent;
            font-size: 1.2rem;
            text-transform: uppercase;
            font-weight: 600;
            font-family: 'Poppins';
            padding-bottom: 1rem;
            position: absolute;
            bottom: 0;    
        }
    }
}
</style>