<template>
  <div class="restaurant-card">
    <div :style="ChangeBackground" class="restaurant-image">

    </div>
    <div class="restaurant-infos">
        <div class="top">
            <p class="name">
                {{ info_restaurant.name }}
            </p>
            <p class="note">
                {{ info_restaurant.note }}
            </p>
        </div>
        <p class="time">
            {{ info_restaurant.drive_time }}
        </p>

    </div>
    
  </div>
</template>

<script>
import { computed } from 'vue'


export default {
    name:"RestaurantCard",
    props:{
        info_restaurant :Object
    },
    setup(props){
        const ChangeBackground = computed(() => {
            return{
                backgroundImage :`url(${props.info_restaurant.image})`
            }
        })
        //return
        return{
            ChangeBackground
        }
    }
}
</script>

<style lang="scss">
.restaurant-card{
    height: 30vh;
    width: 32%;
    .restaurant-image{
        background-image: url('https://cn-geo1.uber.com/image-proc/resize/eats/format=webp/width=550/height=440/quality=70/srcb64=aHR0cHM6Ly9kMXJhbHNvZ25qbmczNy5jbG91ZGZyb250Lm5ldC8zNzg4MDJiMC1jNTI4LTQ4MjktYjBiNS0wY2M2NDBkZjYzY2QuanBlZw==');
        height: 70%;
        background-size: cover;
        background-position: center;
    }
    .top{
        margin: 10px;
        display: flex;
        justify-content: space-between;
        font-size: 0.6rem;
        margin-top:-8px; 
    }
    .note{
        background-color: #eeeeee;
        height: 20px;
        width: 20px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 0.6rem;
        border-radius: 50%;
        
    }
    .time{
        font-size: 0.5rem;
        margin-left: 10px;
        margin-top:-25px;
    }
}

</style>