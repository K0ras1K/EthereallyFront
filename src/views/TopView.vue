<template>
    <MainNavigation />
    <div class="main">
        <div class="theme-text">
            ТОП АКТИВНЫХ УЧАСТНИКОВ
        </div>

        <div class="main-container">
            <div class="table-names-container">
                <div class="left-element text-element">Имя</div>
                <div class="center-element text-element">О себе</div>
                <div class="left-element text-element">АС</div>
            </div>

            <div v-for="index in 10" :key="index" class="element-container">
                <div class="element">
                    {{ emails[index - 1] }}
                </div>
                <div class="element">
                    {{ abouts[index - 1] }}
                </div>
                <div class="element">
                    {{ moneys[index - 1] }}
                </div>

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
  name: "top",
  components: {
    Planets,
    StartButton,
    MainNavigation,
    ApplyButton,
    OkButton
  },
  data() {
    return {
        emails: ["", "", "", "", "", "", "", "", "", ""],
        abouts: ["", "", "", "", "", "", "", "", "", ""],
        moneys: ["", "", "", "", "", "", "", "", "", ""]
    }
  },
  methods: {
    loadLeaderBoard() { 
        axios.get("https://devapi.ethereally.space/public/v1/money/top/get").then(response => {
            console.log(response.data);
            if (response.data.length > 0) {
                for (let i = 0; i < response.data.length; i++) {
                    if (i == 10) {
                        break;
                    }
                    this.emails[i] = response.data[i].email;
                    this.moneys[i] = response.data[i].money;
                    axios.get("https://devapi.ethereally.space/public/v1/users/about/" + response.data[i].email).then(response_1 => {
                        this.abouts[i] = response_1.data.about;
                    })
                }
            }
            console.log(this.emails);
            console.log(this.abouts);
            console.log(this.moneys)
        })
        
    }       
  },
  beforeMount() {
    this.loadLeaderBoard()
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

.text-element {
    color: #FFF;
    text-align: left;
    font-family: Montserrat-Bold;
    font-size: 30px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

.table-names-container {

    width: 1000px;
    display:grid;
    grid-auto-flow:column;
    justify-content:space-around;
}

.element {
    color: #FFF;
    text-align: center;
    font-family: Montserrat-Medium;
    font-size: 15px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

.element-container {
    margin-top: 10px;
    width: 1000px;
    display:grid;
    grid-auto-flow:column;
    justify-content:space-around;
}

.main-container {
    width: 1000px;
    height: 518px;
    border-radius: 90px;
    background: #2b2e35;
    margin-top: 50px;

}

.theme-text {
    color: #FFF;
    font-family: Rimma_sans;
    font-size: 50px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

</style>