<template>
    <div v-if="props" class="stats_card">

        <div class="left-side">
            <h4 class="percentage" :style="`color: ${color}`">{{ percentage }} %</h4>
            <canvas v-if="data" :id="`myChart${cardId}`"></canvas>
            <Loader v-else></Loader>
        </div>
        <div class="right-side">
            <h3 class="balance">{{ title }} Balance</h3>
            <h4 class="amount">{{ amount }} €</h4>
            <button class="card-button" :style="`color: ${color}; border-bottom: 4px solid ${color}`">VIEW MORE</button>
        </div>
        
    </div>
</template>

<script lang="ts" setup>
import Chart from 'chart.js/auto';


const props = defineProps<{
    cardId: number,
    title: string,
    percentage: number,
    color: string,
    amount: number
}>()

const data = {
  datasets: [{
    label: `${props.title}`,
    data: [`${(100 - props.percentage)}`, `${props.percentage}`],
    backgroundColor: [
      'transparent',
      `${props.color}`
    ],
    hoverOffset: 4,
    borderColor: 'transparent',
  }]

};


new Chart(`myChart${props.cardId}`, {
  type: 'pie',
  data: data,
});


</script>

<style lang="scss" scoped>


.stats_card {
    backdrop-filter: blur(3px);
    -webkit-backdrop-filter: blur(3px);
    border-radius: 2rem;
    // box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.2);
    padding: 2rem 1rem 2rem 1rem;
    margin-bottom: 2rem;
    display: flex;
    gap: 10px;
    box-shadow: 0 0px 10px 5px rgba(0, 0, 0, 0.1);

    .left-side {
        width: 30%;
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

    .right-side {
        width: 70%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
        position: relative;

        .balance {
            font-size: 1.1rem;
            font-weight: 400;
            font-family: 'Poppins';
            margin-bottom: 0.5rem;
        }

        .amount {
            font-size: 1.8rem;
            font-weight: 600;
            font-family: 'Poppins';
            margin-bottom: 2rem;
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
            bottom: -1.98rem;    
        }
    }
}
</style>