<template>
  <div class='restaurant-list' v-for="index in round" :key="index">
    <div class="card__header">
      <h3 class="card__header header__title" id="card-title">
        <div class="skeleton skeleton-text"></div>
        <div class="skeleton skeleton-text"></div>
      </h3>
    </div>

    <div class="card__body">
      <div class="card__body body__text" id="card-details">
        <div class="skeleton skeleton-text skeleton-text__body"></div>
      </div>

      <div class="card__body body__img">
        <img class="skeleton" alt="" id="cover-img" />
      </div>
    </div>

    <div class="card__footer" id="card-footer">
      <div class="skeleton skeleton-text skeleton-footer"></div>
    </div>
  </div>
  
</template>

<script>
import { onMounted } from 'vue'
export default {
    name:'preload-list',
    props:{
        round: Array
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

