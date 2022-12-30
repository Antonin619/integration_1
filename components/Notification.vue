<template>
    <div class="notification" :key="id" :style="[isRead? 'background-color: white' : 'background-color: #E5E5E5;']" @click="read()">
        <p class="notif-title">{{ title }}</p>
        <p class="notif-date">{{ date }}</p>
        <p class="notif-description">{{ description }}</p>
        <div v-if="isRead==false" class="unread-dot"></div>
    </div>
    
</template>

<script lang="ts" setup>

const props = defineProps<{
    id: number,
    title: string,
    description: string,
    date: string,
    read: boolean
}>()

const isRead = ref(props.read)

function read() {
    isRead.value = true;
}
</script>   

<style lang="scss" scoped> 
.notification {
    position: relative;
    display: flex;
    flex-direction: column;
    padding: 0.5rem;
    border: 1px solid #E5E5E5;
    border-radius: 0.5rem;
    font-size: 10px;
    margin-bottom: 0.2rem;
    

    .notif-title {
        font-weight: 600;
        font-size: 12px;
    }
}

.unread-dot {
    position: absolute;
    top: -2px;
    right: -2px;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background-color: #FF0000;
    box-shadow: 0px 0px 5px 0px rgba(145, 145, 145, 0.75);
}
</style>