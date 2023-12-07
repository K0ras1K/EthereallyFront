<template>
    <MainNavigation />
    <div class="main">
        <div class="complete-tasks">
            ВЫПОЛНЯЙ ЗАДАНИЯ И ПРОКАЧИВАЙ СКИЛЫ
        </div>
        <div class="choise-container">
            <div v-for="(item, index) in items" :key="index" :class="{ active: activeIndex === index, 'choise-element': true }" @click="setActive(index)">
                <h2 class="choise-element-text choise-element-text-{{ item }}"> {{ item }} </h2>
            </div>
        </div>
        <div class="tasks-container">
            <div class="task-1 task-element">
                <div class="task-1-name task-name">
                    {{ tasks[0] }}
                </div>
                <div class="task-1-about task-about">
                    {{ about[0] }}
                </div>
                <div class="apply-button">
                    <ApplyButton @click="apply(0)"/>
                </div>
                
            </div>
            <div class="task-2 task-element">
                <div class="task-1-name task-name">
                    {{ tasks[1] }}
                </div>
                <div class="task-2-about task-about">
                    {{ about[1] }}
                </div>
                <div class="apply-button">
                    <ApplyButton @click="apply(1)" />
                </div>
            </div>
            <div class="task-3 task-element">
                <div class="task-1-name task-name">
                    {{ tasks[2] }}
                </div>
                <div class="task-3-about task-about">
                    {{ about[2] }}
                </div>
                <div class="apply-button">
                    <ApplyButton @click="apply(2)"/>
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
import axios from 'axios'
export default {
  name: "main",
  components: {
    Planets,
    StartButton,
    MainNavigation,
    ApplyButton
  },
  data() {
    return {
      items: ['Explore', 'Python', 'AI', 'Design', 'Frontend'],
      tasks: ['Task 1', 'Task 2', 'Task 3'],
      about: ['About 1', 'About 2', 'About 3'],
      types: ['GLOBAL', 'PYTHON', 'AI', 'DESIGN', 'FRONTEND'],
      uuids: ["1", "2", "3"],
      activeIndex: 0
    }
  },
  methods: {
    setActive(index) {
      this.activeIndex = index
      this.loadTasks()
      console.log("Load tasks was used!")
    },
    loadTasks() {
        const active_type = this.types[this.activeIndex]
        axios.get("https://devapi.ethereally.space/public/v1/task/get/" + active_type).then(response =>
                 {
                    if (response.data.length == 0) {
                        this.tasks[0] = 'Task 1';
                        this.about[0] = 'About 1';
                        this.tasks[1] = 'Task 2';
                        this.about[1] = 'About 2';
                        this.tasks[2] = 'Task 3';
                        this.about[2] = 'About 3';
                    }
                    if (response.data.length == 1) {
                        this.tasks[0] = response.data[0].name;
                        this.about[0] = response.data[0].about;
                        this.uuids[0] = response.data[0].uuid;
                        console.log("data lenght 1");
                        console.log("response.data[0].name");
                    }
                    if (response.data.length == 2) {
                        this.tasks[0] = response.data[0].name;
                        this.about[0] = response.data[0].about;
                        this.uuids[0] = response.data[0].uuid;
                        this.tasks[1] = response.data[1].name;
                        this.about[1] = response.data[1].about;
                        this.uuids[1] = response.data[1].uuid;
                        console.log("data lenght 2");
                        console.log(response.data[1].uuid);
                    }
                    if (response.data.length > 2) {
                        this.tasks[0] = response.data[0].name;
                        this.about[0] = response.data[0].about;
                        this.uuids[0] = response.data[0].uuid;
                        this.tasks[1] = response.data[1].name;
                        this.about[1] = response.data[1].about;
                        this.uuids[1] = response.data[1].uuid;
                        this.tasks[2] = response.data[2].name;
                        this.about[2] = response.data[2].about;
                        this.uuids[2] = response.data[2].uuid;
                    }
                 })
    },
    apply(task_id) {
        console.log(task_id)
        const request = {email: localStorage.getItem("email"), task_uuid: this.uuids[task_id]}
        axios.post("https://devapi.ethereally.space/public/v1/task/join", request).then(response => {
            
        })
    }
  },
  beforeMount() {
        this.loadTasks()
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

.apply-button {
    margin-top: 10px;
    margin-left: calc((330px - 150px)/2);;
}

.task-name {
    color: #FFF;
    font-family: Montserrat;
    font-size: 25px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

.task-about {
    word-break: break-all;
    margin-top: 10px;
    width: 320px;
    color: #FFF;
    font-family: Montserrat;
    font-size: 15px;
    font-style: normal;
    font-weight: 500;
    line-height: normal;
}

.tasks-container {
    margin-top: 50px;
    width: 1000px;
    display:grid;
    grid-auto-flow:column;
    justify-content:space-around;
    align-items:center;
}

.task-element {
    width: 320px;
    margin-right: 13px;
    text-align: center;
}

.complete-tasks {
    color: #FFF;
    text-align: center;
    font-family: Rimma_sans;
    font-size: 60px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

.choise-container {
    margin-top: 30px;
    display:grid;
    grid-auto-flow:column;
    justify-content:space-around;
    width: 800px;
    margin-left: calc((1000px - 800px)/2);;
}

.choise-element {
    width: 130px;
    height: 52px;
    flex-shrink: 0;
    border-radius: 40px;
    border: 1px solid #FFF;
    align-items: center;
    display: flex;
    justify-content: center;
}

.choise-element-text {
    color: #FFF;
    font-family: Roboto-Medium;
    font-size: 24px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
    display: flex;
    -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Old versions of Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none;
}

.active {
    background: #62D28F;
}



</style>