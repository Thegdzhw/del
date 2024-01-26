<template>
  <header class="header">
    <page-section class="header-info">
      <div class="header-groups">
        <div class="header-group">
          <img style="max-height: 60px" src="/logoo.svg" alt="">
          <div class="header-contact">
            <img src="/tel.svg" alt="">
            <span>7 123 456 78 90</span>
          </div>
        </div>
        <div class="header-group">
          <input type="text" class="header-search" placeholder="Поиск">
        </div>
        <div class="header-group">
          <nuxt-link to="#calculator" style="display: flex; border: none; text-decoration: none; color:black;" class="header-contact">
            <img src="/calc.svg" alt="">
            <span>Калькулятор</span>
          </nuxt-link>
<!--          <button style="display: flex; background-color: rgba(1,1,1,0)" class="login">-->
<!--            <img src="/login.svg" alt="">-->
<!--            <span>Вход</span>-->
<!--          </button>-->
        </div>
      </div>
    </page-section>
    <nav class="header-list">
      <page-section>
        <ul class="nav-list">
          <li class="nav-item">Услуги </li>
          <li class="nav-item">Международные перевозки</li>
          <li class="nav-item">Для бизнеса</li>
          <li class="nav-item">Частным лицам</li>
          <li class="nav-item">О компании</li>
          <li class="nav-item">Блог</li>
          <li class="nav-item">Контакты</li>
          <li class="nav-item">deliverytrans@gmail.com</li>
        </ul>
      </page-section>
    </nav>
  </header>
</template>

<script>
import PageSection from "~/components/common/page-section.vue";

export default {
  components: {PageSection}

}
</script>

<style scoped>
.header-search::placeholder{
  color: white;

}
.header-search{
  background-color: rgba(0,0,0,0);
  padding: 17px 21px;
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: 12px;
  width: 100%;
  /*box-shadow: inherit;*/
}
.header-info{
  display: flex;
  /*flex-direction: column;*/
  align-items: center;
  background: rgba(0, 103, 144, 1);
  height: 101px;

}
.header-groups, .header-group{
  flex-direction: row;
  justify-content: space-between;
}
.header-group:nth-child(2){
  width: 40%;
}
.header-group{
  justify-content: flex-end;
  gap: 20px;
  width: 27%;
}
.header-contact{
  white-space: nowrap;
  gap: 10px;
  padding: 17px 35px;
  min-height: 59px;
  flex-direction: row;
  align-items: center;
  background: rgba(255, 210, 0, 1);
  border-radius: 12px;
}
.login{
  color: white;
  border-radius: 12px;
  border: 1px solid white;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  padding: 21px 19px;
}
.header-list{
  background-color:rgba(2, 139, 193, 1);
  height: 60px;
}
.nav-list{
  padding: 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  color: white;
  list-style: none;
}
</style>
