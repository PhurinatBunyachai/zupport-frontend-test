<template>
  <div class='restaurant-list' v-for="(restaurant, index) in restaurants" :key="index">
    <div class='restaurant-head'>
      <span class='restaurant-name'>{{restaurant.name}}</span>
      <img :src=restaurant.icon alt="icon" width="16" height="16" />
    </div>
    <div class='restaurant-body'>
    <span class='restaurant-address'>{{restaurant.formatted_address}}</span>
    <div class='restaurant-footer'>
        <div class='restaurant-group-rating'>
          <span class='restaurant-rating'>{{restaurant.rating}} </span>
          <i class="fa-solid fa-star icon-rating"></i>
        </div>
        <span :class="`${restaurant.business_status === 'OPERATIONAL' ? 'open' : 'close'} `">{{restaurant.business_status === 'OPERATIONAL' ? 'เปิด' : 'ปิด'}}</span>
    </div>
  </div>
  </div>
</template>

<script>
import { onMounted } from 'vue'
export default {
    name:'restaurants-list',
    props:{
        restaurants: Array,
        isLoading: Boolean
    },

    setup(){
      onMounted(() => {
    })
  }
}
</script>

<style>
  @import './index.css';
</style>

