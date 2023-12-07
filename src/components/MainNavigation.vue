<template>
    <header>
        <nav>
            <!-- <img class="logo" src="img/logo.png"/> -->
            <!-- <AnimatedLogo /> -->
            <img src="logo.png" alt="" class="logo-img">
            <ul v-show="!mobile" class="navigation-texts">
                <li>
                    <router-link class="link" :to="{name: 'main'}">
                        <h1 class="donate-text">Задания</h1>
                    </router-link>
                </li>
                <li>
                    <router-link class="link" :to="{name: 'top'}">
                        <h1 class="donate-text">Рейтинг</h1>
                    </router-link>
                </li>
                <li>
                    <router-link class="link" :to="{name: 'home'}">
                        <h1 class="donate-text">Библиотека</h1>
                    </router-link>
                </li>
                <li>
                    <router-link class="link" :to="{name: 'home'}">
                        <h1 class="donate-text">Магазин</h1>
                    </router-link>
                </li>
            </ul>
            <h1 class="donate-text" @click="logout">Выйти</h1>

            <router-link class="link" :to="{name: 'profile'}">
                    <h1 class="donate-text">Профиль</h1>
            </router-link>

            <h1 class="money-count-text">{{money_count}}</h1>
            <img src="img/coin.png" alt="coin" class="coin">
                

            <!-- <router-link class="link" :to="{name: 'home'}">
                <h1 class="register">Регистрация</h1>
            </router-link> -->
        </nav>
    </header>
</template>

<script>
import StartButton from './buttons/StartButton.vue'
import LoginButton from './buttons/LoginButton.vue'
import DonateButton from './buttons/DonateButton.vue'
import AnimatedLogo from './Logo.vue'
import axios from 'axios'
export default {
    name: "MainNavigation",
    components: {
        StartButton,
        LoginButton,
        DonateButton,
        AnimatedLogo
    },
    data() {
        return {
            money_count: localStorage.getItem('money')
        }
    },

    methods: {
         getMoneyCount() {
            const response = axios.get("https://devapi.ethereally.space/public/v1/money/count/" + localStorage.getItem("email")).then(response => {
                const count = response.data.money;
                // сохраняем токен в localStorage
                this.money_count = count
                localStorage.setItem('money', this.money_count)
                // перенаправляем на другую страницу
            })
            .catch(error => {
                console.error(error);
            });
        },
        load() {
            if (!localStorage.getItem('token')) {
                window.location.href = '/about';
            }
            else {
                //TODO запрос на лоад юзера по токену
                axios.interceptors.request.use(config =>
                 {
                    const token = localStorage.getItem('token');
                    if (token) {
                        config.headers.Authorization = "Bearer ${token}";
                    }
                    return config;
                 })
                 axios.get("https://devapi.ethereally.space/public/v1/users/get/" + localStorage.getItem('token')).then(response =>
                 {
                    localStorage.setItem("email", response.data.email);
                    console.log("Setting to local storage" + response.data.first_name);
                    localStorage.setItem("name", response.data.first_name);
                    localStorage.name = response.data.first_name;
                    localStorage.setItem("telegram", response.data.telegram);
                    localStorage.setItem("role", response.data.role);
                    localStorage.setItem("about", response.data.about);
                 })
            }
        },
        logout(event) {
            localStorage.clear();
            window.location.href = '/about';
        }
    },
    beforeMount() {
        this.load()
        this.getMoneyCount();
    }
}
    

</script>

<style lang="scss" scoped>


@media screen and (min-width: 1000px) {
    nav {
    display:grid;
    grid-auto-flow:column;
    justify-content:space-around;
    align-items:center;
    padding-left: calc((100vw - 1000px)/2);
    margin-top: 20px;
    width:1000px;
    }
}

.login-button {
    // margin-left: 25px;
    // margin-right: 25px;
}

.money-count-text {
    color: #FFF;
    text-align: center;
    font-family: Montserrat-Bold;
    font-size: 25px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

.coin {
    width: 50px;
    height: 50px;
    margin-left: -50px;
}

.start-button {
    // margin-left: 25px;
}

.login-link {
    margin-right: 25px;
}

.register {
    color: #FFF;
    text-align: center;
    font-family: Roboto-Medium;
    font-size: 25px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
    transition: 0.2s;
}

.register:hover {
    color: #62D28F;
    transform: translateY(-2px) scale(1.05);
}

.navigation-texts .navigation-media {
    float: center;
}

.navigation-texts {
    padding-left: -40px;
}

.navigation-texts li {
    display: inline-block;
    margin-right: 30px;
}

// .donate {
//     margin-right: -20px;
// }

.navigation-media li {
    display: inline-block;
    margin-right: 20px;
}


.donate-text {
    text-decoration: none;
    color: white;
    font-family: Roboto-Light;
    font-size: 15px;
    font-style: normal;
    transition: 0.1s;
}

.donate-text:hover {
    color: #62D28F;
    transform: translateY(-2px) scale(1.05);
}

.ds {
    color: #E8E8E8;
    content: url("https://static.ethereally.space/ds.svg");
    margin-right: 50px;
}

.ds:hover {
    content: url("https://static.ethereally.space/ds_hover.svg");
    // transform: translateY(-0.5px) scale(1.05);
}

.tg {
    content: url("https://static.ethereally.space/tg.svg");
    color: #E8E8E8;
    margin-left: -30px;
}

.tg:hover {
    content: url("https://static.ethereally.space/tg_hover.svg");
    // transform: translateY(-0.5px) scale(1.05);
}

.vk {
    content: url("https://static.ethereally.space/vk.svg");
    color: #E8E8E8;
}

.vk:hover {
    content: url("https://static.ethereally.space/vk_hover.svg");
    // transform: translateY(-0.5px) scale(1.05);
}

.login-button {
    transition: 0.1s;
    color: #E8E8E8;
}

.login-button:hover {
    /* ваш hover стиль для login-button */
}

.donate {
    transition: 0.1s;
    color: #E8E8E8;
}

.donate:hover {
    /* ваш hover стиль для donate */
}

.logo {
    transition: 0.1s;
    /* ваш hover стиль для logo */
}

@media screen and (max-width: 600px) {
            nav {
                width: 100%; /* На маленьких экранах меню занимает 100% ширины */
            }

            nav a {
                float: none;
                width: 100%;
                text-align: center;
            }
        }

</style>