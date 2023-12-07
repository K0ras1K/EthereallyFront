<template>
    <div :class="['login-button', className]">
      <div class="text-wrapper">Применить</div>
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
  background: #62D28F;
  height: 20px;
  position: relative;
  width: 100px;
  transition: 0.4s;
  flex-shrink: 0;
}

.login-button .text-wrapper {
    align-items: center;
    justify-content: center;
    position: absolute;
    color: #000;
    font-family: Montserrat-Bold;
    font-size: 12px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
    text-align: center;
    left: 10px;
    top: 3px;
} 

.login-button:hover {
  background: #3ba780;
  box-shadow: 0px 0px 30px 1px #b7bcbd;
  transform: scale(1.1); /* Увеличение размера кнопки */
  transition: 0.4s;
}

.login-button:hover .text-wrapper {
  transform: translateX(2px) scale(1.1); /* Сдвиг и увеличение размера текста */
  transition: 0.4s;
}
</style>
  

