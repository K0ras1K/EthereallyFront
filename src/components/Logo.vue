<template>
    <div :class="['logo-wrapper', className]">
      <div class="image-wrapper">
        <img src="img/logo.png" alt="logo" class="image">
      </div>
      <div class="text-wrapper">
        <div class="logo-text-wrapper">
          <h1 class="logo-text cloud">Cloud</h1>
          <h1 class="logo-text planet">Planet</h1>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "AnimatedLogo",
    props: {
      className: {
        type: String,
        default: "",
      },
    },
  };
  </script>
  
  <style scoped>
  .logo-wrapper {
    position: relative;
    transition: 0.4s;
    display: flex;
    align-items: center;
    width: 270px;
    transition: 0.4s;
  }
  
  .image-wrapper {
    width: 110px;
    height: 110px;
    margin-right: 10px;
    transition: 0.4s;
  }
  
  .text-wrapper {
    flex-grow: 1;
    display: flex;
    align-items: center;
    transition: 0.4s;
  }
  
  .logo-text-wrapper {
    height: 110px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    transition: 0.4s;
  }
  
  .logo-text {
  font-family: "Roboto-Bold";
  font-size: 40px;
  font-style: normal;
  font-weight: 600;
  line-height: 102.5%;
  background: linear-gradient(115deg, #531EEB 0%, #3EECF8 99.25%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  transition: 0.4s;
}

.planet {
  margin-top: -30px;
}
  
  .image {
    width: 110px;
    height: 110px;
  }
  
  .logo-wrapper:hover .image-wrapper {
  transform: scale(1.1);
  transition: 0.4s;
}

.logo-wrapper:hover .logo-text-wrapper .logo-text {
  background: linear-gradient(115deg, #bb96eb 0%, #66C8FF 100%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  /* transform: translateX(3px) scale(1.1); */
  transition: 0.4s;
}
  </style>
  