<script setup>
import { ref } from 'vue';
import BodyMassIndexForm from './components/BodyMassIndexForm.vue';

// reactive variable store BMI result
const bmiResult = ref(null);

// function to handle BMI calculation when event is received
function handleStatsEntered({ height, weight }) {
  if (height > 0 && weight > 0) {
    const bmi = weight / (height * height);
    bmiResult.value = bmi.toFixed(2) // format bmi 2 decimal places
  } else {
    bmiResult.value = 'Invalid input';
  }
}
</script>

<template>

<div class="app-container">

  <h1>Body Mass Index Calculator</h1>
  <!--bmi form component with event listener-->
  <BodyMassIndexForm @stats-entered="handleStatsEntered"/>

  <!--display calculated BMI result-->
  <p v-if="bmiResult !== null">Your BMI: {{ bmiResult }}</p>

  </div>
</template>



<style scoped>

.app-container {
  border: 5px solid blue;
  padding: 20px;
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
}


</style> <!--script, template, file - three components of vue files-->
