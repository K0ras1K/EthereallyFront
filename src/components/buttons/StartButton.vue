<template>
  <div :class="['div-wrapper', className]">
    <div class="text-wrapper">Участвовать</div>
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

<style>
.div-wrapper {
  background: linear-gradient(115deg, #62D28F 0%, #1db351 99.25%);
  border-radius: 30px;
  box-shadow: 0px 0px 30px 1px #62D28F;
  height: 66px;
  position: relative;
  width: 250px;
  transition: 0.4s;
}

.div-wrapper .text-wrapper {
  color: #ffffff;
  font-family: "Montserrat-Medium";
  font-size: 25px;
  font-weight: 600;
  left: 45px;
  letter-spacing: 0;
  line-height: 25.6px;
  position: absolute;
  top: 19px;
  white-space: nowrap;
  width: 146px;
  transition: 0.4s;
}

.div-wrapper:hover {
  background: linear-gradient(115deg, #62D28F 0%, #1db351 99.25%);
  border-radius: 30px;
  box-shadow: 0px 0px 50px 1px #62D28F;
  transform: scale(1.1); /* Увеличение размера кнопки */
  transition: 0.4s;
}

.div-wrapper:hover .text-wrapper {
  transform: translateX(-3px) scale(1.1); /* Сдвиг и увеличение размера текста */
  transition: 0.4s;
}
</style>
