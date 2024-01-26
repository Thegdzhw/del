<template>
    <page-section class="kind-section">
      <h1>Виды перевозимых грузов</h1>
      <div class="kinds-wrapper">
        <div class="kind" v-for="(kind, index) in kinds" :key="index">
          <p>{{kind.title}}</p>
          <p>{{kind.description}}</p>
          <img :src="kind.photo" alt="">
        </div>
      </div>

    </page-section>
</template>

<script>
import PageSection from "~/components/common/page-section.vue";

export default {
  components: {PageSection},
  data() {
    return {
      kinds:[
        {title:"Экспедирование",description:"Принимаем, сопровождаем \n" +
              "и сдаем \n" +
              "груз по утвержденному \n" +
              "маршруту. \n" +
              "Контролируем \n" +
              "правильное \n" +
              "оформление...", photo:"/kind-1.png"},
        {title:"Сборные рефгрузы",description:"Принимаем, сопровождаем \n" +
              "и сдаем \n" +
              "груз по утвержденному \n" +
              "маршруту. \n" +
              "Контролируем \n" +
              "правильное \n" +
              "оформление...", photo:"/kind-2.png"},
        {title:"Перевозка медикаментов",description:"Принимаем, сопровождаем \n" +
              "и сдаем \n" +
              "груз по утвержденному \n" +
              "маршруту. \n" +
              "Контролируем \n" +
              "правильное \n" +
              "оформление...", photo:"/kind-3.png"},
        {title:"Перевозка продуктов питания",description:"Принимаем, сопровождаем \n" +
              "и сдаем \n" +
              "груз по утвержденному \n" +
              "маршруту. \n" +
              "Контролируем \n" +
              "правильное \n" +
              "оформление...", photo:"/kind-4.png"},
        {title:"Перевозка стройматериалов\n",description:"Принимаем, сопровождаем \n" +
              "и сдаем \n" +
              "груз по утвержденному \n" +
              "маршруту. \n" +
              "Контролируем \n" +
              "правильное \n" +
              "оформление...", photo:"/kind-5.png"},
        {title:"Экспедирование",description:"Принимаем, сопровождаем \n" +
              "и сдаем \n" +
              "груз по утвержденному \n" +
              "маршруту. \n" +
              "Контролируем \n" +
              "правильное \n" +
              "оформление...", photo:"/kind-3.png"},
      ]
    }
  }

}
</script>

<style  scoped>
.kind-section h1{
  font-size: 80px;
  font-weight: 700;
  line-height: 109px;
  text-align: center;
  margin-top: 60px;
  margin-bottom: 60px;
}
.kind-section{
  margin-bottom: 100px;
}
.kinds-wrapper{
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
}
.kind{
  width: 45%;
  height: 330px;
  margin-bottom: 30px;
  background: rgba(243, 243, 243, 1);
  border-radius: 12px;
  position: relative;
  padding: 30px;
}
.kind img{
  position: absolute;
  height: 80%;
  /*width: 50%;*/
  right: 0;
  bottom: 0;
}
.kind p:nth-child(1){
  font-size: 26px;
  font-weight: 700;
  line-height: 41px;
  text-align: left;
}
.kind p:nth-child(2){
  font-size: 16px;
  font-weight: 600;
  line-height: 25px;
  letter-spacing: 0em;
  text-align: left;
  color: rgba(102, 117, 130, 1);

}
.kind p{
  width: 45%;
}
</style>
