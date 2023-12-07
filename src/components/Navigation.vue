<template>
    <header>
        <nav>
            <!-- <img class="logo" src="img/logo.png"/> -->
            <!-- <AnimatedLogo /> -->
            <router-link class="link" :to="{name: 'main'}">
                <img src="logo.png" alt="" class="logo-img">
            </router-link>
            <ul v-show="!mobile" class="navigation-texts">
                <li>
                    <router-link class="link" :to="{name: 'home'}">
                        <h1 class="donate-text">Об участниках</h1>
                    </router-link>
                </li>
                <li>
                    <router-link class="link" :to="{name: 'home'}">
                        <h1 class="donate-text">Новости</h1>
                    </router-link>
                </li>
                <li>
                    <router-link class="link" :to="{name: 'home'}">
                        <h1 class="donate-text">Партнеры</h1>
                    </router-link>
                </li>
                <li>
                    <router-link class="link" :to="{name: 'home'}">
                        <h1 class="donate-text">О нас</h1>
                    </router-link>
                </li>
            </ul>

            <router-link class="link" :to="{name: 'register'}">
                <h1 class="register">Регистрация</h1>
            </router-link>
        </nav>
    </header>
</template>

<script>
import StartButton from './buttons/StartButton.vue'
import LoginButton from './buttons/LoginButton.vue'
import DonateButton from './buttons/DonateButton.vue'
import AnimatedLogo from './Logo.vue'
export default {
    name: "Navigation",
    components: {
        StartButton,
        LoginButton,
        DonateButton,
        AnimatedLogo
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