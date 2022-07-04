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
            @keyup="(e) => onUpdateValue({value:e.target.value})"
            @keyup.enter="() => onSearch()"
            />
            <i class="fas fa-arrow-alt-circle-right btn-search" @click="() => onSearch()"></i>
        </div>
         <div class="restaurant">
          <Preload :round="[1,2,3,4,5,6,7,8]" v-if="isLoading"/>
          <Restaurant :restaurants="restaurants" :status="status" v-if="!isLoading && restaurants.length > 0"/>
        </div>
        <NotFound v-if="restaurants.length <= 0 && !isLoading" />
      </div>
    
  </div>
</template>

<script>
import Restaurant from './components/restaurant/List.vue'
import Preload from './components/preload/List.vue'
import NotFound from './components/404/notFound.vue'
import { ref,onMounted } from 'vue'
import axios from 'axios'
export default {
  components: {
    Restaurant,
    Preload,
    NotFound
  },

  setup() {
    let restaurants = ref([])
    let keyword = ref('bang sue')
    let status = ref('ZERO_RESULTS')
    let isLoading = ref(false)
    let config = {
        headers: {'Access-Control-Allow-Origin': '*'}
    };
    onMounted(async () => {
      isLoading.value = true
      await axios.post(
        'http://127.0.0.1:8000/api/restaurants/search', 
        {
          keyword: keyword.value,
        },
        config
        ).then((response) => {
        restaurants.value = response.data.results
      }).catch((error) => {
        console.log('Looks like there was a problem: \n', error);
      });
      isLoading.value = false
    })

    function onUpdateValue({value}){
      keyword.value = value
    }

    const onSearch=async()=>{
       isLoading.value = true
       await axios.post(
        'http://127.0.0.1:8000/api/restaurants/search', 
        {
          keyword: keyword.value,
        },
        config
        ).then((response) => {
        restaurants.value = response.data.results
      }).catch((error) => {
        console.log('Looks like there was a problem: \n', error);
      });
      isLoading.value = false
    }


    return{restaurants,keyword,onSearch,onUpdateValue,isLoading,status}
  }

}
</script>

<style>
  @import './assets/css/restaurant.css';
</style>