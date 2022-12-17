<template>
  <div class="loginCard">
    <div>
      Hur många julenötter (oavsett knäckstatus) fanns det på Pinetorpet på juldagsmorgonen?
    </div>
    <input type="text" ref="inputText"/>

    <button v-if="tries > 1" type="button" @click="buttonIsPressed = !buttonIsPressed">
      {{!buttonIsPressed ? ' Det här var knepigt, ge mig en ledtråd!' :  'Tack!'}}
    </button>

    <div v-if="buttonIsPressed">
<div>
      Först och främst, för er messerschmittrar: 
</div>
<div></div>
      Nej, mandeln är visserligen ingen nöt, men den är en JULENÖT, baske oss!'Vilket är vad som efterfrågas.
<div></div>
      Med den kunskapen, räkna bakifrån.
<div></div>
      40 kvar i påsen på slutet, minus 18 från ekorren blir 22.
<div></div>
      Lägg sedan till alla andra nötter.
<div></div>
      Tänk på att katterna får tre HALVOR VAR. Lurigt där.
<div></div>
      Lycka till!
    </div>



    <button type="button" @click="submit">
      Skicka in
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const emit = defineEmits<{
  (e: 'correctAnswer'): void
}>()

const inputText = ref<HTMLInputElement>()
const buttonIsPressed = ref<boolean>(false)
const tries = ref<number>(0)

const submit = () => {
  if(inputText.value && inputText.value.value === '264') {
    console.log(inputText.value.value)
    emit('correctAnswer')
  } else {
    tries.value = tries.value + 1
  }
}
</script>

<style scoped>
.loginCard {
  font-family: Arial, Helvetica, sans-serif;
  display: flex;
  flex-direction: column;
  justify-content: center; 
  align-items: center;
  gap: 24px;
  min-height: 100;
  width: 400px;
  background-color: aquamarine;
  border-radius: 10px;
  padding: 24px;
}
</style>
