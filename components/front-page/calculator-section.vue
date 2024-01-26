<template>
  <div>
    <page-section>
      <h1 class="calculator-title">Калькулятор</h1>
      <div class="calculator-wrapper">
        <div class="sbor-checkout">
          <p @click="isSbor" class="sbor-sbor" :class="{'active-sbor': sbor}">Сборные грузы</p>
          <p @click="isNesbor" class="sbor-sbor" :class="{'active-sbor' : nesbor}">Несборные грузы</p>
        </div>
        <div class="calculate-items">
          <div class="calculate-item_wrapper c-item">
            <img src="/a.svg" alt="">
            <div class="calc-item">
              <p style="color: #C7C7C7">Откуда</p>
              <div class="calculate">
                <input type="text" placeholder="Название города" v-model="into">
              </div>
            </div>
          </div>
          <div class="calculate-item_wrapper c-item">
            <img src="/b.svg" alt="">
            <div class="calc-item">
              <p style="color: #C7C7C7">Куда</p>
              <div class="calculate">
                <input type="text" placeholder="Название города" v-model="to">
              </div>
            </div>
          </div>
          <calculate-item class="c-item" :edinica="v" :image="vImg" :title="vTitle" @number="saveVolume"/>
          <calculate-item class="c-item" :edinica="kg" :image="vesImg" :title="vesTitle" @number="saveWeight"/>
        </div>
        <h2>Дополнительные опции</h2>
        <div class="dop">
          <div class="calculate-items">
            <calculate-item :edinica="g" :image="gImg" :title="gTitle" @number="saveGabarites"/>
            <calculate-item :edinica="c" :image="cImg" :title="cTitle" @number="saveCount"/>
          </div>
        </div>
        <div style="flex-direction: row; justify-content: space-between"><h2>Cтрахование груза</h2> <h2>Доставка груза в тепле</h2></div>
        <div class="strah-wrapper">
          <div class="strah-checkout">
            <p @click="isStrah" class="strah-strah" :class="{'active-strah': strah}">Застраховать</p>
            <p @click="isNestrah" class="strah-strah" :class="{'active-strah' : nestrah}">Нет</p>
          </div>
          <calculate-item :edinica="str" :image="strahImage" :title="strahTitle" @number="saveStrah"/>
          <div class="strah-checkout">
            <p @click="isHot" class="strah-strah" :class="{'active-strah': hot}">В тепле</p>
            <p @click="isNehot" class="strah-strah" :class="{'active-strah' : nehot}">Нет</p>
          </div>
        </div>
        <button @click="calculateThis" style="width: 100%;margin: 0 auto; border:none" class="sbor-sbor active-sbor button">Расчитать</button>
      </div>
    </page-section>
    <div v-if="result" class="calculator-result">
      <p>Доставка обойдется вам в {{Math.round(price)}} рублей</p>
      <button @click="result=false" style="color:black;position: absolute; right: 15px;top: 15px; border: none;background-color: rgba(0,0,0,0)">X</button>
      <nuxt-link to="#form" class="form-submit" @click="result=false">
        Оставить заявку
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import PageSection from "~/components/common/page-section.vue";
import CalculateItem from "~/components/front-page/calculator/calculate-item.vue";

export default {
  data(){
    return{
      into:"",
      to:"",
      strah:true,
      nestrah:false,
      hot:true,
      nehot:false,
      sbor:true,
      nesbor:false,
      kg:"кг",
      v:"м3",
      vImg:"/v.svg",
      vTitle:"Объем",
      vesImg:"/ves.svg",
      vesTitle:"Вес",
      g:"м",
      gImg:"/gabarity.svg",
      gTitle:"Максимальные габариты",
      c:"шт",
      cImg:"/count.svg",
      cTitle:"Количество мест",
      str:"руб",
      strahImage:"/r.svg",
      strahTitle:"Заявленная стоимость",
      volume:'',
      weight:'',
      count:"",
      gabarites:"",
      strahprice:"",
      result: false,
      price:0
    }
  },
  components: {CalculateItem, PageSection},
  methods:{
    isHot(){
      this.hot = true
      this.nehot = false
    },
    isNehot(){
      this.hot = false
      this.nehot = true
    },
    isStrah(){
      this.strah = true
      this.nestrah = false
    },
    isNestrah(){
      this.strah = false
      this.nestrah = true
    },
    isSbor(){
      this.sbor = true
      this.nesbor = false
    },
    isNesbor(){
      this.sbor = false
      this.nesbor = true
    },
    saveWeight(number){
      this.weight = number
    },
    saveVolume(number){
      this.volume = number
    },
    saveCount(number){
      this.count = number
    },
    saveGabarites(number){
      this.gabarites = number
    },
    saveStrah(number){
      this.strahprice = number
    },
    calculateThis(){
      this.result = true
      this.price= (this.volume * 100) + (this.weight*98) + (this.gabarites * 87) + (this.count * 15) + (this.into.length * 30) + (this.to.length * 30)
      if (this.hot){
        this.price += 500
      }
      if (this.strah){
        this.price += this.strahprice * 1.5
      }
      if (this.sbor) {
        this.price *= 1.1
      }
      console.log('Объем:'+this.volume + 'Вес:'+ this.weight + 'Габариты:' + this.gabarites + 'Количество мест:' + this.count + "Откуда" + this.into.length)
    }
  },
  // emits: ["number"],

}
</script>

<style scoped>
.c-item{
  width: 25%;
}
.button:hover{
  background-color: rgba(0, 126, 176, 1)!important;
}
.dop{
  width: 50%;
}
.calculate-items{
  flex-direction: row;
  justify-content: space-between;
  margin-bottom: 50px;
}
.sbor-checkout{
  flex-direction: row;
  padding: 10px;
  border-radius: 12px;
  background-color: rgba(0, 126, 176, 1);
  width: 60%;
  margin-bottom: 50px;
}
.sbor-sbor{
  color: white;
  width: 50%;
  padding: 8px 58px;
  text-align: center;
}
.strah-checkout{
  background: rgba(214, 234, 255, 1);
  flex-direction: row;
  padding: 10px;
  border-radius: 12px;
  width: 35%;
}
.strah-checkout:nth-child(3){
  width: 25%;
}
.strah-strah{
  color: rgba(102, 117, 130, 1);
  width: 50%;
  padding: 27px 30px;
  text-align: center;
}
.strah-strah.active-strah{
  background: rgba(2, 139, 193, 1);
  border-radius: 6px;
  color: white;
}
.sbor-sbor.active-sbor{
  background: rgba(0, 103, 144, 1);
  border-radius: 6px;

}
.strah-wrapper{
  flex-direction: row;
  align-items: center;
  margin-bottom: 50px;
  justify-content: space-between;

}
.calculator-title{
  font-size: 80px;
  font-weight: 700;
  line-height: 109px;
  text-align: left;
  margin-bottom: 60px;
}
.calculator-wrapper{
  padding: 30px 60px;
  background-color: white;
  border-radius: 12px;
  margin-bottom: 60px;
}
.calculator-wrapper h2{
  font-size: 20px;
  font-weight: 700;
  line-height: 27px;
  text-align: left;
  color:rgba(102, 117, 130, 1);
  margin-bottom: 30px;
  margin-right: 45px;
  margin-left: 30px;
}
.calculator-result{
  position: fixed;
  border-radius: 16px;
  inset: 0;
  margin-top: 10vh;
  margin-left: 15vw;
  width: 70vw;
  height: 80vh;
  background: rgba(214, 234, 255, 1);
  display: flex;
  align-items: center;
  justify-content: center;
}
.form-submit{
  padding: 18px 22px;
  background-color: rgba(255, 210, 0, 1);
  border: 0;
  border-radius: 12px;
  text-decoration: none;
  color:black;
  margin-top:80px;
}
</style>
