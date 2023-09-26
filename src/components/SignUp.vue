<template>
<h1>Sign Up</h1>

<div class="resgister">
    <input type="text" v-model="name" placeholder="Enter Name" />
    <input type="text" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />
    <button v-on:click="signUp()">Sign Up</button>
    <p>
        <router-link to="/login">Login</router-link>
    </p>
</div>
</template>

<script>
import axios from 'axios'
import { onMounted } from 'vue';
import { RouterLink } from 'vue-router';
export default {
    name: 'signUp',
    data() {
        return {
            name: '',
            email: '',
            password: ''
        };
    },
    methods: {
        async signUp() {
            let result = await axios.post("http://localhost:3000/user", {
                name: this.name,
                email: this.email,
                password: this.password
            });
            console.warn(result);
            if (result.status == 201) {
                localStorage.setItem("user-info", JSON.stringify(result.data));
                this.$router.push({ name: 'Home' });
            }
        }
    },
    Mounted() {
        let user = localStorage.getItem('user-info');
        if (user) {
            this.$router.push({ name: 'Home' });
        }
    },
    components: { RouterLink }
}
</script>

<style>
.resgister input {

    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid #ed8b00;

}

.resgister button {

    width: 320px;
    height: 40px;
    border: 1px solid #ed8b00;
    background: #ed8b00;
    color: #fff;
    cursor: pointer;
}
</style>
