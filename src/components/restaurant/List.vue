<template>
  <div class='restaurant-list' v-for="(restaurant, index) in restaurants" :key="index">
     <div class='restaurant-image'>
        <img src='https://placehold.jp/650x350.png'/>
     </div>
     <span class='restaurant-name'>{{restaurant.name}}</span>
  </div>
</template>

<script>
import { onMounted } from 'vue'
export default {
    name:'restaurants-list',
    props:{
        restaurants: Array
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

