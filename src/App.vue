<template>
  <div style="height: 100vh; width: 100vw;">
    <div v-if="answeredCorrect" class="videoContainer">
      <video width="800" height="500" controls autoplay>
        <source src="./movie.mp4" type="video/mp4">
      </video>
    </div>
    <div v-if="!answeredCorrect" class="container welcome">
      <div style="padding: 70px">
        <h1 style="font-size: 50px; font-family: Verdana, sans-serif">Välkommen till Eva och Jonatans julkort!</h1>
      </div>
    </div>
    <div v-if="!answeredCorrect" class="container login">
      <Login @correctAnswer="answeredCorrect = true"/>
    </div>
  </div>
</template>

<script>
import Login from "./components/Login.vue";
export default {
  data() {
    return {
      answeredCorrect: false
    }
  },
  components: {
    Login
  }
}
</script>

<style scoped>
.videoContainer {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  background-color: #668c6f;
}

.container {
  font-family: Verdana, sans-serif;
  color: #668c6f;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 40%;
}

.welcome {
  justify-content: center;
}

.login {
  justify-content: flex-start;
}
</style>
