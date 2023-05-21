<script setup>
import { ref } from 'vue';
import LoginForm from './components/LoginForm.vue';
import SignupForm from "./components/SignupForm.vue"
const hideLogin = ref(false)
const userDetails = ref({})
const showDetails = ref(false)
const updateHide = (value) => {
  hideLogin.value = value
}

const signupDetails = details =>{
  hideLogin.value = false
  userDetails.value = details
  showDetails.value = true
}

</script>

<template>
<div class="home-container">
  <LoginForm v-show="!hideLogin" @hideLogin="updateHide"/>
  <SignupForm :signupDetails="signupDetails" v-show="hideLogin" />
  <h1 v-if="showDetails">{{ userDetails }}</h1>
</div>

</template>

<style scoped>
.home-container{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}
</style>
