<template>
  <div class="home">
    <div class="header">
      <img src="https://d3i4yxtzktqr9n.cloudfront.net/web-eats-v2/ee037401cb5d31b23cf780808ee4ec1f.svg" alt="">
      <div class="wripprer--input">
        <input v-model="user_search_restaurant" type="text" placeholder="What Do You Need">
      </div>
      <div class="search"></div>

     
     
    </div>
    <div class="bannier"></div>
    <RestaurantRow v-for="(data , i) in date_restaurant" :key="i" :three_restaurant="data"/>
  </div>
</template>

<script>
//import 

import BDD from '../BDD.js'
import  {onMounted , ref ,watch} from 'vue'
// componenets
import RestaurantRow from '../RestaurantRow.vue';

export default {
    name:'HomeRestaurant',
    components:{
      RestaurantRow
    },
    setup(){
      class Restaurant{
        constructor (name,note,image,drive_time){
        this.name = name
        this.note =note
        this.image = image
        this.drive_time =drive_time
      }
    }

    let date_restaurant = ref([]);
    let all_restaurant =[]

    const makeDataRestaurant = () =>{
      let three_restaurant =[];

      for (const  restaurant of BDD){
        const  new_restaurant = new Restaurant(restaurant.name, restaurant.note,restaurant.image,restaurant.drive_time)
        // make all restaurant array
        all_restaurant.push(new_restaurant);
        
        if(three_restaurant.length ===2){
          three_restaurant.push(new_restaurant);
          date_restaurant.value.push(three_restaurant);
          three_restaurant = [];
        }else{
          three_restaurant.push(new_restaurant);
        }
      }
    }
    // user search restaurant

    let user_search_restaurant = ref('');
    let search_restaurant =ref([])

    watch(user_search_restaurant, new_value=> {
      let regex = RegExp(new_value);

      let new_search_restaurant = all_restaurant.filter(restaurant => regex.test(restaurant.name));
      search_restaurant = new_search_restaurant
      

    })



    onMounted(makeDataRestaurant);
    //return 
    return{
      date_restaurant,
      user_search_restaurant,
      search_restaurant,
    }
    
  },

}
</script>

<style lang="scss">
.home{
  .header{
    width:100% ;
    height: 100%;
    display: flex;
    justify-content: space-between;
    img{
      width:200px;
    }
    .wripprer--input{
      position: relative;
      .input{
      background-color: #f6f6f6;
      height:100px ;
      width:50px ;
      border: none;
      outline: none;
      padding-left: 20px;
       }
       .search{
        position: absolute;
        top: 10%;
        width: 50%;
        height: 400px;
        background-color: #ffffff;
        border: solid 1px red;
        background-color: red;
       }
    }
  
    .bannier{
      height:200px ;
      width: 100px;
      background-image: 'https://stock.adobe.com/search?k=food+delivery&asset_id=301327108';
      background-size: cover;
      background-position: bottom ;
      background-color: red;
    }
  }
}

</style>