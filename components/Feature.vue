<template>
    <div class="feature-container">
        <div v-if="props" :style="`height:${featureSize}px; background-image: url(${image})`" class="feature">
        
        </div>
        <div v-if="props.description" class="feature_description">
            {{ props.description }}
        </div>
        <button v-if="props.button_text" class="feature_button">
            {{ props.button_text }} <client-only><font-awesome-icon class="pl-4" icon="fa-solid fa-arrow-right" /></client-only>
        </button>
    </div>
</template>

<script lang="ts" setup>

const props = defineProps<{
    image: string | null,
    description: string | null,
    button_text: string | null,
    button_link: string | null,
    size: 'small' | 'medium' | 'large' | null
}>()

const featureSize = ref(300);

function setSize() {

    if (props.size) {

        switch (props.size) {
            case 'small':
                featureSize.value = 200;
                break;
            case 'medium':
                featureSize.value = 300;
                break;
            case 'large':
                featureSize.value = 500;
                break;
        }
    }
}

setSize();

</script>

<style lang="scss" scoped>

.feature-container {

    border-radius: 1rem;
    overflow: hidden;
    box-shadow: 0 10px 15px 5px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(3px);
    margin-bottom: 4rem;

    .feature {
        
        overflow: hidden;
        background-size: cover;
        background-position: center;

    }

    .feature_description {
        background-color: white;
        border-top-left-radius: 1rem;
        border-top-right-radius: 1rem;
        margin-top: -1rem;
        padding: 1rem;
        box-shadow: 0 0px 20px 5px rgba(0, 0, 0, 0.1);
        border-bottom: 1px solid rgb(233, 233, 233);
        font-size: 12px;
    }


    .feature_button {
            background-color: white;
            color: rgb(71, 0, 185);
            border: none;
            border-bottom-left-radius: 1rem;
            border-bottom-right-radius: 1rem;
            padding: 1rem 2rem 1rem 2rem;
            font-size: 1.2rem;
            font-weight: 700;
            width: 100%;
            cursor: pointer;
            padding-left: 2rem;
    }
}
</style>