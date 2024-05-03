<script setup>
import {ref} from "vue";

const {myList} = defineProps(['myList']);

const inputData = ref('');

console.log(myList);

const handler = ()=>{
  if (inputData.value=='' || inputData.value.length<3){
    alert('لطفا لیست خود را خالی پر نکنید و بالای 2 کلمه بنویسید');
  }else {
    myList.push(inputData.value);
    inputData.value = '';
    localStorage.setItem('lists', JSON.stringify(myList));
  }

}

</script>

<template>

  <div class="margin-top:10px">
    <input :value="inputData"
           @input="event=>inputData=event.target.value"
           type="text" placeholder="Write your task..."/>
    <button @click="handler">+</button>
  </div>

</template>


<style>

</style>