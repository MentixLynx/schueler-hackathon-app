<script setup>
import Login from './components/Login.vue';
import Registration from './components/Registration.vue';
import Home from './components/Home.vue';
import Liked from './components/Liked.vue';
import { ref } from 'vue'

let isLoggedIn = ref(false);
let isRegister = ref(false);
let isHome = ref(false);
let isLiked = ref(false);

const switchToLiked = () => {
  console.log("switch");
  isHome.value = !isHome.value;
  isLiked.value = !isLiked.value;
};

const toHome = () => {
  isLoggedIn.value = false;
  isRegister.value = false;
  isHome.value = true;
}

const switchToRegister = () => {
  console.log("switch");
  isLoggedIn .value = !isLoggedIn .value;
  isRegister.value = !isRegister.value;
};

</script>

<template>
  <div v-if="!isLoggedIn && !isRegister && !isHome && !isLiked" class="flex flex-col">
    <h1 class="p-4 mx-auto text-3xl font-bold">
      This is a login dialogue
    </h1>
    <div class="flex flex-row mx-auto">
      <button @click="isLoggedIn = !isLoggedIn" class="p-4 m-4 font-sans font-bold text-white rounded-lg bg-sky-500 hover:bg-sky-700">Login</button>
      <button @click="isRegister = !isRegister" class="p-4 m-4 font-sans font-bold text-white rounded-lg bg-sky-500 hover:bg-sky-700">Registration</button>
    </div>
  </div>
  <div v-if="isLoggedIn" class="flex flex-row">
    <Login @switch-to-register="switchToRegister" @login-success="toHome" class="mx-auto"></Login>
  </div>
  <div v-if="isRegister" class="flex flex-row">
    <Registration @switch-to-login="switchToRegister" @register-success="toHome" class="mx-auto"></Registration>
  </div>
  <div v-if="isHome" class="flex flex-row">
    <Home @switch-to-liked="switchToLiked" class="mx-auto"></Home>
  </div>
  <div v-if="isLiked" class="flex flex-row">
    <Liked @switch-to-home="switchToLiked" class="mx-auto"></Liked>
  </div>
  
</template>

<style scoped>
</style>
