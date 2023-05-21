<script setup>
import { ref } from 'vue';

defineEmits(["hideLogin"])
const isLoggedIn = ref(false)

</script>

<template>
    <div class="form-container">
        <FormKit type="form" submit-label="Login" @submit="isLoggedIn = true">
            <FormKit type="email" validation="required" name="email" label="Email"/>
            <FormKit type="password" validation="required" name="password" label="Password"/>
        </FormKit>
        <FormKit v-if="!isLoggedIn" type="button" @click="$emit('hideLogin',true)">Sign Up</FormKit>
        <p v-if="isLoggedIn">Log in success</p>
    </div>
</template>

<style scoped>
.form-container{
    width: 35vw;
    padding: 40px;
    border-radius: 10px;
    box-shadow: 0px 4px 16px 0px #bfbfbf;
}
</style>