<script setup lang="ts">
import { ref } from 'vue'

const currentDate:Date = new Date();
const hour = ref(currentDate.getHours());
const minute = ref(60-currentDate.getMinutes());
const seconds = ref(60-currentDate.getSeconds());

const props = defineProps(['endDate']);

function countDays(){
  const start: Date = new Date();
  const end: Date = new Date(props.endDate);
  const timeDifference: number = end.getTime() - start.getTime();
  return Math.ceil(timeDifference / (1000 * 3600 * 24));
}

function countHours(){
  return 24-hour.value;
}

setInterval(() => {
  const test:Date = new Date();
  minute.value = 60-test.getMinutes();
  seconds.value = 60-test.getSeconds();
}, 1000)

</script>

<template>
  <h1>Ferdig med eksamen om!</h1>
  <br>
  <p>{{countDays()}} daga <br> {{countHours()}}  tima <br> {{minute}} minutta <br> {{seconds}} sekunda <br></p>
</template>

<style scoped>
h1{
  color: #B8E3F2;
  margin: 0; 
}

p{
    color: #B8E3F2;
    font-size: 3em;
    margin: 0;
}

img{
  border-radius: 1%;
}

</style>
