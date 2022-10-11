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
  <button class="button button_responsive" @click="incrementor">aumentar</button>
  <button class="button button_responsive" @click="decremented">disminuir</button>
  <button class="button button_responsive" @click="restart">restart</button>
  <div class="add_items">
    <button class="button button_responsive " :disabled="noBtn" @click="mostrarNum">añadir</button>
    <ul class="list-group mt-4 button_responsive" >
      <li v-for="( num ) in liNum" key="index" 
      class="list-group-item"
      >
      {{ num }}</li>
    </ul>
  </div>
</template>
<style>
</style>
