<template>
  <div class="loginCard">
    <div>
      Hur många julenötter (oavsett knäckstatus) fanns det på Pinetorpet på
      juldagsmorgonen?
    </div>
    <input v-model="inputText" type="text" ref="inputText" class="input"/>
    <div v-if="tries > 0" style="color: #ab453e; font-weight: 700">Fel! Försök Igen!</div>
    <button
      v-if="tries > 1 && !buttonIsPressed"
      class="button"
      type="button"
      @click="buttonIsPressed = !buttonIsPressed">
      Det här var knepigt, ge mig en ledtråd!
    </button>
    <div v-else-if="buttonIsPressed">
      <div>Först och främst, för er messerschmittrar:</div>
      Nej, mandeln är visserligen ingen nöt, men den är en JULENÖT, baske
      oss!'Vilket är vad som efterfrågas. Med den kunskapen, räkna bakifrån. 40
      kvar i påsen på slutet, minus 18 från ekorren blir 22. Lägg sedan till
      alla andra nötter. Tänk på att katterna får tre HALVOR VAR. Lurigt där.
      Lycka till!
    </div>
    <button type="button" class="button" @click="submit">Skicka in</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      buttonIsPressed: false,
      tries: 0,
      inputText: ''
    }
  },
  methods: {
    submit() {
       if (this.inputText === "264") {
        this.$emit("correctAnswer");
      } else {
        this.tries = this.tries + 1;
      }
    },
  },
  mounted() {
    this.$refs.inputText.focus()
  }
}
</script>

<style scoped>
.loginCard {
  color: #1a251d;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 24px;
  min-height: 100;
  width: 400px;
  background-color: #668c6f;
  border-radius: 10px;
  padding: 24px;
}
.input {
  border-radius: 5px;
  border: none;
  height: 40px;
  font-family: Verdana, sans-serif;
  outline: none;
  color: #1a251d;
}
.button {
  border-radius: 5px;
  border: none;
  height: 30px;
  background-color: white;
  color: #1a251d;
  font-family: Verdana, sans-serif
}
.button:hover {
  background-color: #eceaea;
}
</style>
