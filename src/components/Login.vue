<template>
<h1>Sign Up</h1>

<div class="login">
    <input type="text" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />
    <button v-on:click="login()">Login</button>
    <p>
        <router-link to="/sign-up">Sign Up</router-link>
    </p>
</div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'Login',

    data() {
        return {

            email: '',
            password: ''
        }
    },
    methods: {
        async login() {
            let result = await axios.get(
                'http://localhost:3000/user?email=${this.email}&password=${this.password}'
            )
            console.log(result)
        }
    }
}
</script>

<style>
.login input {

    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid #ed8b00;

}

.login button {

    width: 320px;
    height: 40px;
    border: 1px solid #ed8b00;
    background: #ed8b00;
    color: #fff;
    cursor: pointer;
}
</style>
