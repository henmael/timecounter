<script setup lang="ts">
import { ref } from 'vue'
import Auka from '../assets/uka-a.jpg'
import Kuka from '../assets/uka-k.jpg'
import Uuka from '../assets/uka-u.jpg'

const currentDate:Date = new Date();
const hour = ref(currentDate.getHours());
const minute = ref(60-currentDate.getMinutes());
const seconds = ref(60-currentDate.getSeconds());


function countDays(endDate){
  const start = new Date();
  const end = new Date(endDate);
  const timeDifference = end - start;
  return Math.ceil(timeDifference / (1000 * 3600 * 24));
}

function countHours(){
  return 24-hour.value;
}

setInterval(() => {
  const test:Date = new Date();
  minute.value = 60-test.getMinutes();
  seconds.value = 60-test.getSeconds();
  countMinutes
}, 1000)

</script>

<template>
  <img :src="Uuka" />
  <img :src="Kuka" />
  <img :src="Auka" />
  <h1>{{countDays('2025-10-02')}}:{{countHours()}}:{{minute}}:{{seconds}}</h1>
</template>

<style scoped>
h1{
  color: #B8E3F2;
  margin: 0; 
}

p{
    color: #B8E3F2;
    font-size: 8em;
    margin: 0;
}

img{
  border-radius: 1%;
}

</style>
