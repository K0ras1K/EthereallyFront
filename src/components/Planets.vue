<template>
  <div class="planet-container" @mouseover="startRotation" @mouseout="stopRotation" @mounted="setInitialStyles">
    <div class="sun" :style="{ backgroundImage: `url('img/planets/sun.png')` }"></div>
    <div v-for="(planet, index) in planets" :key="index" :class="'planet planet-' + (index + 1)" :style="planet.style">
      <img :src="`img/planets/planet${index + 1}.png`" alt="Planet">
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      planets: [
        { angle: 0, distance: 240, style: {} },
        { angle: 80, distance: 250, style: {} },
        { angle: 160, distance: 265, style: {} },
        { angle: 260, distance: 235, style: {} },
      ],
      rotationInterval: null,
    };
  },
  methods: {
    setInitialStyles() {
      this.planets.forEach((planet, index) => {
        const x = Math.cos((planet.angle * Math.PI) / 180) * planet.distance + 150;
        const y = Math.sin((planet.angle * Math.PI) / 180) * planet.distance + 150;
        planet.style = {
          transform: `translate(${x}px, ${y}px)`,
        };
      });
    },
    startRotation() {
      this.rotationInterval = setInterval(() => {
        this.planets.forEach((planet, index) => {
          planet.angle += 1;
          const x = Math.cos((planet.angle * Math.PI) / 180) * planet.distance + 150;
          const y = Math.sin((planet.angle * Math.PI) / 180) * planet.distance + 150;
          planet.style = {
            transform: `translate(${x}px, ${y}px)`,
          };
        });
      }, 20);
    },
    stopRotation() {
      clearInterval(this.rotationInterval);
    },
  },
  mounted() {
    // Вызывать при загрузке страницы
    this.setInitialStyles();
  },
};
</script>
  
  <style scoped>
  .planet-container {
    position: relative;
    width: 300px;
    height: 300px;
    margin: 50px auto;
  }
  
  .sun {
    width: 55px;
    height: 52px;
    background-size: cover;
    position: absolute;
    top: 80%;
    left: 85%;
    transform: translate(-50%, -50%) scale(5.2);
  }
  
  .planet {
    background-size: cover;
    position: absolute;
  }
  
  .planet img {
    /* width: 100%;
    height: 100%; */
    /* transform: scale(5); */
    transform: scale(0.8);
  }

  .planet-1 {
    /* Additional styling for planet 2 if needed */
    transform: scale(5.1);
  }
  
  .planet planet-2 {
    /* Additional styling for planet 2 if needed */
    transform: scale(5.3);
  }
  
  .planet planet-3 {
    /* Additional styling for planet 3 if needed */
    transform: scale(5.5);
  }
  
  .planet planet-4 {
    /* Additional styling for planet 4 if needed */
    transform: scale(5.7);
  }
  </style>
  