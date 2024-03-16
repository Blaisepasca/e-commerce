<template>
    <div class="restaurant--row">
        <div class="title">
            <h2>Online restaurant</h2>
            <div class="wrapper-card">
                <restaurant-card v-for="(card, index) in three_restaurant" :info_restaurant='card' :key="index" />
            </div>

        </div>
    </div>

</template>

<script>

import RestaurantCard from './RestaurantCard.vue'
export default {
    name: "RestaurantRow",
    components: {
        RestaurantCard,
    },
    props: {
        three_restaurant: Array
    },
    
}
</script>

<style lang="scss">
.restaurant--row {
    .title {
        font-size: 15px;
    }

    .wrapper-card {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
}
</style>