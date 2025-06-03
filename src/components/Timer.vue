<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  year: Number, 
  month: Number, 
  day: Number,
  hours: Number, 
  minutes: Number, 
  second: Number
});

const currentDate:Date = new Date();
const lastDate: Date = new Date(props.year, props.month, props.day, props.hours, props.minutes, props.second);

const hour = ref(currentDate.getHours()-lastDate.getHours());
const minute = ref(60-currentDate.getMinutes()-lastDate.getMinutes());
const seconds = ref(60-currentDate.getSeconds()-lastDate.getSeconds());


function countDays(){
  const timeDifference: number = lastDate.getTime() - currentDate.getTime();
  return Math.ceil(timeDifference / (1000 * 3600 * 24));
}

function countHours(){
  return 24-hour.value;
}

setInterval(() => {
  const test:Date = new Date();
  minute.value = 60-test.getMinutes()-lastDate.getMinutes();
  seconds.value = 60-test.getSeconds()-lastDate.getSeconds();
}, 1000)

</script>

<template>
  <h1>Malin, Pål og Luna kjem om...</h1>
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
