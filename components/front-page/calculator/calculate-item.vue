<template>
  <div class="calculate-item_wrapper">
    <img :src="image" alt="">
    <div class="calc-item">
      <p style="color: #C7C7C7">{{title}}</p>
      <div class="calculate">
        <button @click="minus" class="calc-button"><img src="/minus.svg" alt=""></button>
        <input style="width: 15%" v-model.number="number" type="text" @change="$emit('number', number)" @input="onInput">
        <p>{{edinica}}</p>
        <button @click="plus" class="calc-button"><img src="/plus.svg" alt=""></button>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      number:10
    }
  },
  props:{
    image:{type: String},
    title:{type:String},
    edinica:{type:String}
  },
  methods:{
    plus(){
      this.number+=1
      this.$emit('number', this.number);
    },
    minus(){
      this.number-=1
      this.$emit('number', this.number);
    },
    onInput(event) {
      this.number = event.target.value.replace(/[^0-9]/g, '');
    }
  },
  mounted() {
    this.$emit("number", this.number)
  }
}
</script>

<style>
.calculate-item_wrapper{
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 10px;
}
.calculate{
  flex-direction: row;
  gap: 3px;
  align-items: center;
}
.calc-button{
  border: none;
  padding: 0;
  background: rgba(0,0,0,0);
}

</style>
