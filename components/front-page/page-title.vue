<template>
  <div class="front-title">
    <page-section>
      <h1>Доставим ваш груз в любую точку России</h1>
      <p>Доставляем сборный груз от 1кг по всей стране
        узнай стоймость перевозки прямо сейчас</p>
    </page-section>
    <img class="front-page_car" src="/car.png" alt="">
  </div>

</template>

<script>
import PageSection from "~/components/common/page-section.vue";

export default {
  components: {PageSection}

}
</script>

<style  scoped>
.front-title{
  position: relative;
  background: rgba(0, 103, 144, 1);
  color: white;
  /*height: 70vh;*/
}
.front-title h1{
  margin-top: 70px;
  width: 50%;
  font-family: Nunito, sans-serif;
  font-size: 80px;
  font-weight: 700;
  line-height: 109px;
  text-align: left;
}
.front-title p{
  width: 50%;
  font-family: Nunito, sans-serif;
  font-size: 20px;
  font-weight: 600;
  line-height: 37px;
  text-align: left;
  margin-bottom: 140px;
}
.front-page_car{
  position: absolute;
  right: 0;
  top: 0;
  height: 100%;
}
</style>
