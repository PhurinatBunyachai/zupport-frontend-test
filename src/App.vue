<template>
  <div class="container">
    <div class="head-section">
      <span class="keyword">{{keyword ? keyword : 'กินอะไรดี'}}</span>
    </div>
    
      <div class="restaurant-section">
        <div class="search">
          <input 
            type="text" 
            :value="keyword" 
            :placeholder="keyword ? keyword : 'กินอะไรดี' " 
            @keyup="(e) => onSearch({value:e.target.value})"
            />
        </div>
         <div class="restaurant">
          <Restaurant :restaurants="restaurants" />
        </div>
      </div>
    
  </div>
</template>

<script>
import Restaurant from './components/restaurant/List.vue'
import { ref,onMounted } from 'vue'
export default {
  components: {
    Restaurant
  },

  setup() {
    let restaurants = ref([{}])
    let keyword = ref('bang sue')
    onMounted(() => {
      restaurants.value = [{name: 'test'},{name: 'eiei'},{name: 'eiei22'}]
    })

    function onSearch({value}){
      keyword.value = value
    }


    return{restaurants,keyword,onSearch}
  }

}
</script>

<style>
  @import './assets/css/restaurant.css';
</style>