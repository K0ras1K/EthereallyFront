<template>
    <div :class="['login-button', className]">
      <div class="text-wrapper">Войти</div>
    </div>
</template>
  
<script>
  export default {
    name: "DivWrapper",
    props: {
      className: {
        type: String,
        default: "",
      },
    },
  };
</script>
  
<style scoped>
.login-button {
  background: #D9D9D9;
  border-radius: 15px;
  height: 50px;
  position: relative;
  width: 150px;
  transition: 0.4s;
}

.login-button .text-wrapper {
  color: #5A5A5A;
  font-family: "Roboto-Regular";
  font-size: 25px;
  font-weight: 600;
  left: 2px;
  letter-spacing: 0;
  line-height: 25.6px;
  position: absolute;
  top: 12px;
  white-space: nowrap;
  width: 146px;
  transition: 0.4s;
}

.login-button:hover {
  background: #b7bcbd;
  border-radius: 15px;
  box-shadow: 0px 0px 30px 1px #b7bcbd;
  transform: scale(1.1); /* Увеличение размера кнопки */
  transition: 0.4s;
}

.login-button:hover .text-wrapper {
  transform: translateX(2px) scale(1.1); /* Сдвиг и увеличение размера текста */
  transition: 0.4s;
}
</style>
  

   <!-- <template>
    <div
      :class="['property-hover-wrapper', propertyState.property1, className]"
      @mouseenter="handleMouseEnter"
      @mouseleave="handleMouseLeave"
    >
      <div class="overlap-group">
        <div v-if="propertyState.property1 === 'hover'" class="text-wrapper">Войти</div>
        <template v-else>Войти</template>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "PropertyHoverWrapper",
    props: {
      property1: {
        type: String,
        default: "one",
        validator: function (value) {
          return ["one", "hover"].indexOf(value) !== -1;
        },
      },
      className: {
        type: String,
        default: "",
      },
    },
    data() {
      return {
        propertyState: {
          property1: this.property1,
        },
      };
    },
    methods: {
      handleMouseEnter() {
        this.propertyState.property1 = "hover";
      },
      handleMouseLeave() {
        this.propertyState.property1 = "one";
      },
    },
  };
  </script>
  
  <style>
  .property-hover-wrapper {
    width: 150px;
  }
  
  .property-hover-wrapper .text-wrapper {
    color: #5a5a5a;
    font-family: "Gilroy-Medium", Helvetica;
    font-size: 30px;
    font-weight: 500;
    left: 43px;
    letter-spacing: 0;
    line-height: 30.7px;
    position: absolute;
    top: 19px;
    white-space: nowrap;
    width: 84px;
    transition: 0.4s;
  }
  
  .property-hover-wrapper.one {
    background-color: #d9d9d9;
    border-radius: 15px;
    height: 66px;
    position: relative;
  }
  
  .property-hover-wrapper.hover {
    height: 72px;
  }
  
  .property-hover-wrapper.one .overlap-group {
    color: #5a5a5a;
    font-family: "Gilroy-Medium", Helvetica;
    font-size: 25px;
    font-weight: 500;
    left: 40px;
    letter-spacing: 0;
    line-height: 25.6px;
    position: absolute;
    top: 19px;
    white-space: nowrap;
    width: 70px;
  }
  
  .property-hover-wrapper.hover .overlap-group {
    background-color: #d9d9d9;
    border-radius: 15px;
    height: 72px;
    left: -10px;
    position: relative;
    top: -6px;
    width: 169px;
  }
  </style> -->