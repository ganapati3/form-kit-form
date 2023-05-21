<script setup>
import { ref } from 'vue';

const props = defineProps({
    signupDetails:Function,
})

const fields = ref({})
const createUserDetails = (fileds) => {
    fields.value = fileds
    props.signupDetails(fileds)
}
</script>

<template>
    <div class="form-container">
        <FormKit type="form" submit-label="Sign Up" @submit="createUserDetails" >
            <FormKit type="text" name="name" label="Full Name" validation="required" placeholder="Full name"/>
            <FormKit type="email" validation="required" name="email" label="Email" placeholder="example@gmail.com"/>
            <FormKit type="password"
                    name="password"
                    label="Password"
                    placeholder="Enter a new password"
                    validation="required"
                    validation-visibility="live"/>
            <FormKit type="password"
                    name="password_confirm"
                    label="Confirm password"
                    placeholder="Confirm your new password"
                    validation="required|confirm"
                    validation-visibility="live"
                    validation-label="Password confirmation"/>
            <FormKit name="Gender" label="Gender" type="radio" validation="required" :options="{
                male:'Male',
                female:'Female'

            }"/>
            
        </FormKit>
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