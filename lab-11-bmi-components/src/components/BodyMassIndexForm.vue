<script setup>
import { ref } from 'vue'

// BodyMassIndexForm.vue does not receive props from App.vue
//defineProps({
//  msg: String,
//})

// add reactive variables for height and weight - height in meters weight in kilograms
const height = ref('')
const weight = ref('')

// define stats-entered event emitter
const emit = defineEmits(['stats-entered'])

// function to emit height weight data
function submitStats() {
  emit('stats-entered', { height: Number(height.value), weight: Number(weight.value) })
}

</script>

<template>

  <div class="form-container">
  
  <h2>Enter you details!</h2>
  
  
  <!--height input-->
    <label>
      Height (meters):
      <input v-model="height" type="number" placeholder="Enter height (in meters)" />
    </label>
    <!--weight input-->
    <label>
      Weight: (in kilograms):
      <input v-model="weight" type="number" placeholder="Enter weight (in kilograms)" />
    </label>

      <!--button to submit height and weight-->
      <button @click="submitStats">Calculate</button>
      
    </div>

</template>

<script>
import { ref } from 'vue';

// add reactive variables for height and weight
const height = ref('')
const weight = ref('')

// define stats-entered event emitter
const emit = defineEmits(['stats-entered']);

// function - emit height and weight data
function submitStats() {
  emit('stats-entered', { height: Number(height.value), weight: Number(weight.value) })
}

</script>

<style scoped>

.form-container {
  border: 3px solid red;
  padding: 10px;
  text-align: center;
}
label {
  display: block;
  margin-bottom: 10px;
}
button {
  display: block;
  margin-top: 10px
}


</style>
