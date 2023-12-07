<template>
    <Navigation />
    <div class="main">
        <div class="register-container">
            <div class="auth-type">
                <div class="auth-type-text">
                    <router-link class="link" :to="{name: 'login'}">
                        ВХОД
                    </router-link>
                </div>
                <div class="auth-type-text">
                    <router-link class="link" :to="{name: 'register'}">
                        РЕГИСТРАЦИЯ
                    </router-link>
                </div>
            </div>
            <div class="input-block">
                <input type="email" v-model="email" placeholder="Электронная почта" class="input-container email">
                <input type="password" v-model="passwod" placeholder="Пароль" class="input-container passwod">
            </div>
            <div class="line">

            </div>
            <div class="register-button-container">
                <LoginButton @click="login" />
            </div>
        </div>
    </div>

</template>

<script>

import Planets from "../components/Planets.vue"
import StartButton from "../components/buttons/StartButton.vue"
import RegisterButton from "../components/buttons/RegisterButton.vue"
import LoginButton from "../components/buttons/LoginButton.vue"
import Navigation from "../components/Navigation.vue"
import axios from 'axios'
export default {
  name: "login",
  components: {
    Planets,
    StartButton,
    RegisterButton,
    LoginButton,
    Navigation
  },
  data() {
    return {
        API_URL: 'https://devapi.ethereally.space/public/v1/users/login',
        email: '',
        password: '',
    }
    },

    methods: {
        login(event) {
            const request = {email: this.email, password: this.passwod}
            const response = axios.post(this.API_URL, request).then(response => {
                const token = response.data.token;
                // сохраняем токен в localStorage
                localStorage.setItem('token', token);
                // перенаправляем на другую страницу
                window.location.href = '/';
            })
            .catch(error => {
                console.error(error);
            });
        },
        validateToken() {
            if (localStorage.getItem('token')) {
                window.location.href = '/about';
            }
        },
    },
    beforeMount() {
        this.validateToken()
    }
};


</script>

<style scoped>

@media screen and (min-width: 1000px) {
    .main {
        padding-top: 30px;
        align-items:center;
        padding-left: calc((100vw - 1000px)/2);
        width:1000px;
        /* position: absolute; */
        /* display: flex;   */

    }
}

.register-button-container {
    margin-left: calc((458px - 150px)/2);
    margin-top: 30px;
}
.line {
    margin-top: 10px;
    width: 273px;
    height: 0.5px;
    background: #000;
    margin-left: calc((458px - 273px)/2);
}

.input-container {
    width: 273px;
    height: 40px;
    border-radius: 7px;
    background: #F8F1FF;
    border-color: #F8F1FF;
    flex-shrink: 0;
    outline: none;
    box-shadow: 0 0 0 0px;
    margin-top: 20px;
    margin-left: calc((458px - 273px)/2);
}

input:focus {
 outline: none;
}

.auth-type {
    display:grid;
    grid-auto-flow:column;
    /* justify-content:space-between; */
}

.auth-type-text {
    color: #000;
    text-align: center;
    font-family: Montserrat-Medium;
    font-size: 14px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
    text-transform: uppercase;
    margin-top: 30px;
}

.register-container {
    width: 458px;
    height: 542px;
    flex-shrink: 0;
    border-radius: 30px;
    background: #F4F4EE;
    box-shadow: 0px 4px 17px 0px rgba(0, 0, 0, 0.17);
    margin-left: calc((1000px - 458px)/2);
}


</style>