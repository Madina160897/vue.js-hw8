<script setup>
import Purchase from './components/Purchase.vue'
import Income from './components/Income.vue'
import Statistics from './components/Statistics.vue';
</script>

<template>
  <div>
    <h1>SPA-приложения</h1>
    <div class="box">
      <Purchase />
      <Income />
    </div>
    <Statistics />
  </div>
</template>

<style>
body {
  background-color: #c5f3f3;
}

h1 {
  margin-top: 50px;
  text-align: center;
  font-size: 40px;
  color: rgb(52, 51, 59);
  font-weight: 900;
}

.box{
  display: flex;
    flex-direction: row;
    justify-content: space-around;
    width: 100%;
}
</style>
