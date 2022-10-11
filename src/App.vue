<script setup>
import { ref, computed } from 'vue'
const vittoLym = "Staff Lym."
/* contador */ 
const Counter = ref(0);
const incrementor = ()=>{
Counter.value ++;
}
const decremented =() =>{
Counter.value --;
}
const restart =() =>{
  Counter.value = Counter.value - Counter.value
};
/* color de contador */
const Counterclass = computed(() =>{
  if (Counter.value === 0){
    return 'black'
  }
  else if (Counter.value < 0){
    return 'red'
  }
  else(Counter.value > 0); {
    return 'green'
  }
  });
/*Btn add*/ 
const liNum = ref([]);
const mostrarNum = () =>{
  liNum.value.push(Counter.value)
  };
const noBtn = computed(()=> {
const numSearch = liNum.value.find(num => num === Counter.value)
return numSearch ? true : numSearch == 0 ? true : false;
});
</script>
<template>
  <h1>{{vittoLym}}</h1>
  <h2 :class="Counterclass"> {{Counter}}</h2>
  <button class="button" @click="incrementor">aumentar</button>
  <button class="button" @click="decremented">disminuir</button>
  <button class="button" @click="restart">restart</button>
  <div>
    <button class="add" :disabled="noBtn" @click="mostrarNum">añadir</button>
    <ul class="list-group mt-4" >
      <li v-for="( num ) in liNum" key="index" 
      class="list-group-item"
      >
      {{ num }}</li>
    </ul>
  </div>
</template>
<style>

h1{
  padding-left: 50px;
  color: rgba(255, 255, 255, 0.87);
}
h2{
  padding-left: 40px;
}
.red{
  color: red;
}
.green {
  color: green;
}
.black{
  color: black;
}
.add{
  margin-top: 20px;
  margin-left: 45px;
}
.list-group-item{
  background-color: #242424;
  color: #fafafa;
  border: 1px solid #000;
  left: 20px;
}

</style>
