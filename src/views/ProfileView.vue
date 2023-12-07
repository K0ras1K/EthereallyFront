<template>
    <MainNavigation />
    <div class="main">
        <div class="hello-text">
            ЗДРАВСТВУЙТЕ, {{ this.name }}
        </div>

        <div class="main-container">
            <div class="left-container">
                <div class="top-element">
                    <div class="left-element">
                        <div class="left-element-text element-text">Имя</div>
                        <div class="left-element-content element-content"> {{ name }}  </div>
                    </div>
                    <div class="center-element">
                        <div class="center-element-text element-text">Роль</div>
                        <div class="center-element-content element-content"> {{ role }} </div>
                    </div>
                    <div class="right-element">
                        <div class="right-element-text element-text">Telegram</div>
                        <div class="right-element-content element-content"> {{ telegram }} </div>
                    </div>
                </div>
                <div class="bottom-element">
                    <div class="right-element-text element-text">О Себе</div>
                    <div class="bottom-element-input">
                        <input v-model="message" class="element-input" placeholder="О себе" />
                        <OkButton @click="updateAbout" class="ok-button" />
                        
                    </div>
                </div>
            </div>

            <div class="right-container">


            </div>
        </div>
    </div>

</template>

<script>

import Planets from "../components/Planets.vue"
import StartButton from "../components/buttons/StartButton.vue"
import MainNavigation from "../components/MainNavigation.vue"
import ApplyButton from "../components/buttons/ApplyButton.vue"
import OkButton from "../components/buttons/OkButton.vue"
import axios from 'axios'
export default {
  name: "profile",
  components: {
    Planets,
    StartButton,
    MainNavigation,
    ApplyButton,
    OkButton
  },
  data() {
    return {
        name: "name",
        telegram: "telegram",
        role: "role",
        email: "email",
        message: ""
    }
  },
  methods: {
    loadFromLocalStorage() {
        this.name = localStorage.getItem("name");
        this.telegram = localStorage.getItem("telegram");
        this.role = localStorage.getItem("role");
        this.email = localStorage.getItem("email");
    },
    updateAbout(event) {
        const request = {email: this.email, about: this.message}
        axios.post("https://devapi.ethereally.space/public/v1/users/update", request).then(response =>
        {
            localStorage.setItem("about", this.message);
        })
    }
  },
  beforeMount() {
    this.loadFromLocalStorage()
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

.ok-button {
    margin-top: 10px;
    margin-left: -20px;
}

.bottom-element-input {
    display:grid;
    grid-auto-flow:column;
    align-items:center;
}

.left-container {
    width: 500px;
}

.bottom-element {
    margin-top: 30px;
}

.element-text {
    color: #FFF;
    text-align: center;
    font-family: Montserrat-Bold;
    font-size: 30px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

.element-input {
    margin-top: 10px;
    width: 300px;
    margin-left: calc((500px - 300px)/2 - 75px);
}

.element-content {
    color: #FFF;
    text-align: center;
    font-family: Montserrat;
    font-size: 15px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

.top-element {
    display:grid;
    grid-auto-flow:column;
    align-items:center;
}

.right-container {    
    width: 500px;
}

.hello-text {
    width: 1000px;
    color: #FFF;
    font-family: Rimma_sans;
    font-size: 60px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

.main-container {
    width: 1000px;
    height: 518px;
    flex-shrink: 0;
    border-radius: 90px;
    background: #2b2e35;
    margin-top: 50px;
    display:grid;
    grid-auto-flow:column;
    justify-content:space-around;
    align-items:center;
}


</style>