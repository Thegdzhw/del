<template>
  <div class="main">
    <page-title/>
    <kind-section/>
    <form-section/>
    <calculator-section id="calculator"/>
  </div>
</template>

<script>
import PageTitle from "~/components/front-page/page-title.vue";
import KindSection from "~/components/front-page/kind-section.vue";
import FormSection from "~/components/front-page/form-section.vue";
import CalculatorSection from "~/components/front-page/calculator-section.vue";

export default {
  components: {CalculatorSection, FormSection, KindSection, PageTitle}

}
</script>

<style  scoped>
.main{
  background: rgba(243, 249, 255, 1);

}
</style>
