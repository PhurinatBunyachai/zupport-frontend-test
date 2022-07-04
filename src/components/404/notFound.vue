<template>
  <div class='not-found'>
    <div class='containner'>
        <i class="fas fa-times-circle icon"></i>
        <span class='label'>ไม่พบรายการ</span>
    </div>
  </div>
</template>

<script>
import { onMounted } from 'vue'
export default {
    name:'not-found',
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

