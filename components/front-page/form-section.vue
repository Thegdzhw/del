<template>
  <div class="form-section" id="form">
    <page-section>
      <p>Нет времени разбираться?</p>
      <p>Подскажем!</p>
      <div class="form-wrapper">
        <div class="form-item">
          <label for="form-input">Я хочу привезти</label>
          <input v-model="what" id="form-input" type="text" placeholder="Например: Кухонный уголок" class="form-input">
        </div>
        <div class="form-item">
          <label for="form-input">Откуда - куда</label>
          <input v-model="where" id="form-input" type="text" placeholder="Например: Москва - Владивосток" class="form-input">
        </div>
        <div class="form-item">
          <label for="form-input">Телефон</label>
          <input v-model="number" id="form-input" placeholder="+7 ___ ___ __ __" type="text" class="form-input">
        </div>
      </div>
      <div class="form-buttons">
        <div class="form-politic">
          <input type="checkbox" v-model="isPolitic">
          <span>Согласие на обработку персональных данных</span>
        </div>
        <button class="form-submit" @click="completed">
          Оставить заявку
        </button>
      </div>
    </page-section>
  </div>
  <div v-show="isComplete" class="complete">
    <div class="complete-content">Заявка отправлена!</div>
  </div>
</template>

<script>
import PageSection from "~/components/common/page-section.vue";

export default {
  components: {PageSection},
  data(){
    return {
      what:"",
      where:"",
      number:"",
      isComplete:false,
      isPolitic:false
    }
  },
  methods:{
    completed(){
      if (this.isPolitic){
        this.isComplete = true
        this.what = ""
        this.where = ""
        this.number = ""
        setTimeout(()=>{
          this.isComplete = false
        }, 1000)
      }
    }
  }

}
</script>

<style scoped>
.form-section{
  background: url("/form-background.svg") no-repeat;
  height: 100%;
  padding-top: 60px;
}
.form-section p{
  color: white;
  font-size: 80px;
  font-weight: 700;
  line-height: 109px;
  text-align: center;
}
.form-section p:nth-child(2){
  margin-bottom: 50px;
}
.form-wrapper{
  flex-direction: row;
  justify-content: space-between;
}
.form-item{
  width: 32%;
  position: relative;
  margin-bottom: 48px;
}
.form-item label{
  position: absolute;
  left: 21px;
  top: 21px;
  /*z-index: 10;*/
}
.form-input{
  padding: 50px 21px 16px 21px;
  border-radius: 12px;
  border: none;
}
.form-politic{
  flex-direction: row;
  gap: 10px;
  align-items: center;
  color: white;

}
.form-buttons{
  flex-direction: row;
  justify-content: space-between;
  margin-bottom: 117px;
}
.form-submit{
  padding: 18px 22px;
  background-color: rgba(255, 210, 0, 1);
  border: 0;
  border-radius: 12px;
}
.complete {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #FFFFFF;
  display: flex;
  align-items: center;
  justify-content: center;
}

.complete-content {
  font-family: 'TT Commons Pro Variable', sans-serif;
  white-space: nowrap;
  color:green;
  font-size: 50px;
  height: 100px;
  margin: 0 auto;
}
</style>
