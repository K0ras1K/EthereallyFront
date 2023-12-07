<template>
    <Navigation />
    <div class="main">
        <div class="hello">
            <div class="left-part">
                <div class="join">
                    <img src="img/web.png" alt="web" class="logo-img">
                </div>
            </div>

            <div class="planets">
                <div class="name-text">
                    <img src="img/name.png" alt="ethereally" class="text-name-img">
                </div>
                <div class="about-text">
                    Многофункциональная платформа развития навыков  молодых IT специалистов
                </div>
            </div>
        </div>
        <div class="collab">
            <img src="img/l40xmpit.png" alt="l.40 x mpit" class="collab-img">
        </div>

        <div class="members">
            <div class="members-left">
                <div class="members-left-text">
                    Более <span class="text-bold">1000</span> участников
                </div>
                <img src="img/members-left.png" alt="" class="members-left-img">
            </div>
            <div class="members-right">
                <div class="members-right-text">
                    Проекты в <span class="text-bold">10</span> регионах РФ
                </div>
                <img src="img/members-right.png" alt="" class="members-right-img">
            </div>
        </div>

        <div class="interesting">
            <div class="interesting-main-text">
                Заинтересовался?
            </div>
            <div class="join-main-text">
                Присоединяйся к нам!
            </div>
            <div class="last-double-block">
                <div class="comlete-tasks-container">
                    <div class="complete-tasks-text">
                        Выполняй задания Зарабатывай акселькоины Получай ценные призы Прокачивай свои навыки Заявляй о себе
                    </div>
                </div>
                <div class="join-button-container">
                    <div class="join-button">
                        <router-link class="link" :to="{name: 'register'}">
                            <StartButton />
                        </router-link>
                        
                    </div>
                </div>
            </div>
        </div>
        

    </div>

</template>

<script>

import Planets from "../components/Planets.vue"
import StartButton from "../components/buttons/StartButton.vue"
import Navigation from "../components/Navigation.vue"
export default {
  name: "home",
  components: {
    Planets,
    StartButton,
    Navigation
  },
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

.join-button {
    margin-left: 150px;
    margin-top: 40px;
}

.complete-tasks-text {
    color: #FFF;
    font-family: Montserrat-Medium;
    font-size: 20px;
    font-style: normal;
    font-weight: 600;
    line-height: normal; 
    width: 300px;
}

.comlete-tasks-container {
    width: 500px;
}

.join-button-container {
    width: 500px;
}

.last-double-block {
    width: 1000px;
    display:grid;
    grid-auto-flow:column;
    justify-content:space-between;
}

.interesting {
    margin-top: 30px;
}

.interesting-main-text {
    color: #FFF;
    font-family: Rimma_sans;
    font-size: 60px;
    font-style: normal;
    font-weight: 700;
    line-height: 120%; /* 72px */
    text-align: right;
    margin-left: 150px;
    line-height: normal;
}

.join-main-text {
    color: #FFF;
    text-align: right;
    font-family: Montserrat-Medium;
    font-size: 30px;
    font-style: normal;
    font-weight: 900;
    line-height: normal;
}   

.members-left-text .text-bold {
    color: #62D28F;
    font-family: Montserrat-Bold;
}

.members-left-text {
    color: #FFF;
    font-family: Montserrat-Medium;
    font-size: 60px;
    font-style: normal;
    font-weight: 500;
    line-height: 120%; /* 72px */
}

.members-right-text .text-bold {
    color: #62D28F;
    font-family: Montserrat-Bold;
}

.members-right-text {
    color: #FFF;
    font-family: Montserrat-Medium;
    font-size: 60px;
    font-style: normal;
    font-weight: 500;
    line-height: 120%; /* 72px */
}


.members-left {
    width: 500px;
    align-items: center;
    margin-top: 50px;
}

.members-right {
    width: 500px;
    align-items: center;
    margin-top: 50px;
}

.members-left-text {
    text-align: center;
}
.members-right-text {
    text-align: center;
}

.members-left-img {
    margin-left: 24px;
    margin-top: 20px;
}

.members-right-img {
    margin-left: 24px;
    margin-top: 20px;
}

.members {
    margin-top: 30px;
    border-radius: 90px;
    /* opacity: 0.2; */
    background: #4d4f55;
    width: 1000px;
    height: 600px;
    display:grid;
    grid-auto-flow:column;
    justify-content:space-between;
}

.text-name-img {
    width: 600px;
}

.collab {
    margin-top: 10px;
    width:1000px;
    
}

.collab-img {
    margin-left: 173px;
}

.start-button {
    margin-top: 50px;
    /* transform: scale(1.1); */
}

.about-text {
    color: #ACBEBE;
    text-align: right;
    font-family: Montserrat-Bold;
    font-size: 30px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}
.name-text {
    color: #62D28F;
    text-align: center;
    font-family: Rimma_sans;
    font-size: 60px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
    width:600px;
}

.left-part {
    width: 300px;
}

.logo-img {
    width: 300px;
    height: 300px;
}

.planets {
    width: 600px;
    /* height: 500px; */
    margin-left: 100px;
}

.hello {
    margin-top: 30px;
    text-align: center;
    display:grid;
    grid-auto-flow:column;
    justify-content:space-between;
    /* align-items:center; */
}

.join-text-h {
    font-family: Roboto-Bold;
    font-size: 65px;
    /* font-style: normal; */
    font-weight: 700;
    line-height: 102.5%; /* 66.625px */
    background: linear-gradient(115deg, #531EEB 0%, #3EECF8 99.25%);
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    text-align: left;
    width: 648px;
}


.join-adv-h {
    width: 648px;
    color: #FFF;
    font-family: Roboto-Light;
    font-size: 30px;
    font-style: normal;
    font-weight: 500;
    line-height: 102.5%; /* 30.75px */
    text-align: left;
}



</style>