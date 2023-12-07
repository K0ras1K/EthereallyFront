<template>
    <div
      class="property-animation-wrapper"
      @mouseenter="handleMouseEnter"
      @mouseleave="handleMouseLeave"
    >
      <div class="text-wrapper">
        <h1 class="donate">Донат</h1>
      </div>
      <img
        class="file"
        :class="{ 'is-hovered': state.isMouseOver }"
        alt="File"
        :src="state.property1 === 'one' ? 'img/coin.svg' : 'img/coin.svg'"
      />
    </div>
  </template>
  
  <script scoped>
  export default {
    name: "DonateButton",
    data() {
      return {
        state: {
          property1: "one",
          isMouseOver: false,
        },
      };
    },
    methods: {
      handleMouseEnter() {
        this.state.isMouseOver = true;
        this.state.property1 = "animation";
      },
      handleMouseLeave() {
        this.state.isMouseOver = false;
        this.state.property1 = "one";
      },
    },
  };
  </script>
  
  <style>

  .text-wrapper h1 {
    color: #ff9400;
  }

  .property-animation-wrapper {
    display: flex;
    align-items: center;
    position: relative;
    width: 151px;
    transition: 0.4s;
  }
  
  .property-animation-wrapper .file {
    height: 35px;
    width: 36px;
    margin-left: 5px;
    transition: transform 0.4s ease, scale 0.4s ease;
  }
  
  .property-animation-wrapper .file.is-hovered {
    animation: spin 1.5s linear infinite;
    transform: translateY(-1px) scale(1.05);
  }
  
  @keyframes spin {
    from {
      transform: rotateY(0deg);
    }
    to {
      transform: rotateY(360deg);
    }
  }
  
  .property-animation-wrapper .text-wrapper {
    font-family: Roboto-Medium;
    font-size: 25px;
    margin-right: 5px;
    transition: transform 0.4s ease, scale 0.4s ease, transform 0.1s ease;
  }
  
  .property-animation-wrapper.is-hovered .text-wrapper {
    transform: translateY(-1px) scale(1.05);
  }
  
  .property-animation-wrapper.is-hovered .file {
    transform: translateY(-1px) scale(1.05);
  }
  
  .property-animation-wrapper .property-1-animation {
    color: #ff9400;
  }
  
  .donate {
    color: #ff9400;
    font-family: Roboto-Light;
    font-size: 25px;
    font-style: normal;
  }

  .donate:hover {
    transform: translateY(-1px) translateX(1px) scale(1.05);
    color: #f5b353;
  }
  </style>
  