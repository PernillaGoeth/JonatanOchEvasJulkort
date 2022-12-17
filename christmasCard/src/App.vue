<template>
  <div v-if="answeredCorrect">VIDEO</div>
  <div v-if="!answeredCorrect" class="container welcome">
    <div style="padding: 70px;">
      <h1 style="font-size: 50px;">Välkommen till Eva och Jonatans julkort!</h1>
    </div>
  </div>
  <div v-if="!answeredCorrect" class="container login">
    <Login @correctAnswer="answeredCorrect = true"/>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Login from "./components/Login.vue";
const answeredCorrect = ref<boolean>(false)
</script>

<style scoped>
.container {
  font-family: Arial, Helvetica, sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 50%;
}

.welcome {
  justify-content: flex-end;
}

.login {
  justify-content: flex-start;
}
</style>
