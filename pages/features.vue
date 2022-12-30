<template>
    <div class="features p-8">
        <h1>Features</h1>

        <h2>Check the market charts </h2>
        <h5 class="mb-10">Detailed charts are available for free !</h5>

        <Feature image="./_nuxt/assets/features_1.png" size="large" :description="null" button_text="Discover" :button_link="null"/>

        <h2 >Discover every crypto market</h2>
        <h5 class="mb-10">All markets are here !</h5>

        <Feature image="./_nuxt/assets/features_2.jpg" size="medium" description="Checkout our new features ! On our platform, you can now see every cryptocurrency markets for free, you just have to subscribe !" button_text="Check this out" :button_link="null"/>

        <h2 >Your feedback</h2>
        <h5 class="mb-10">See our happy customers feedbacks !</h5>

        <Feature image="./_nuxt/assets/features_3.jpg" size="medium" description="Our customers are very happy about our platform, you can leave a review if you want, it helps us a lot ! Don't hestitate to rate our work out of 5 stars and let us know what you think about it with a comment !" :button_text="null" :button_link="null"/>
    </div>
</template>

<script lang="ts" setup>
import Feature from '~~/components/Feature.vue';


</script>

<style lang="scss" scoped>

</style>