<template>
    <div v-if="props" class="collaborator">
        <div class="pp-role">
       <img class="shadow-custom" :src="picture || './_nuxt/assets/user.jpg'" alt="">
       <h3 v-if="description">{{ role }}</h3>
    </div>
         <div class="collaborator-info">
                <h2>{{firstname}} {{lastname}}</h2>
                <h3 v-if="description == null" class="mb-12 opacity-50">{{ role }}</h3>
              <p v-if="description" :class="portfolio? 'collaborator-description mb-10' : 'collaborator-description mb-2'">{{description}}</p>
              
        </div>
        <button v-if="portfolio"><a  :href="portfolio" target="_blank">Portfolio <client-only><font-awesome-icon class="pl-4" icon="fa-solid fa-arrow-right" /></client-only></a></button>
    </div>
    <Loader v-else></Loader>
</template>

<script lang="ts" setup>

const props = defineProps<{
    id: number,
    picture: string | null,
    firstname: string,
    lastname: string,
    role: string,
    description: string | null,
    portfolio: string | null,
}>()

</script>

<style lang="scss" scoped>
.collaborator {
    display: flex;
    backdrop-filter: blur(10px);
    box-shadow: 0 0px 20px 5px rgba(0, 0, 0, 0.1);
    border-radius: 1rem;
    padding: 1rem;
    position: relative;
    margin-bottom: 4rem;
    background-color: white;

    .pp-role {
        
        min-width: 100px;
        margin-right: 2rem;
        text-align: center;

            img {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            margin-right: 20px;
            margin-bottom: 20px;
        }

        h3 {
            font-size: 14px;
            opacity: 0.5;
            margin-bottom: 1rem;
        }
    }
    

    .collaborator-info {
        display: flex;
        gap: 1rem;
        flex-direction: column;

            .collaborator-description {
                font-size: 12px;
            }
    }

    button {
        position: absolute;
        bottom: -1.75rem;
        right: 2rem;
        background-color: rgb(71, 0, 185);
        border-radius: 1rem;
        padding: 1rem 2rem 1rem 2rem;
        box-shadow: 0 0px 20px 5px rgba(0, 0, 0, 0.1);
        font-weight: 800;
        color: white;
    }
}

.shadow-custom {
    box-shadow: 0 5px 20px 5px rgba(0, 0, 0, 0.15);
    border: 2px solid white
}
</style>