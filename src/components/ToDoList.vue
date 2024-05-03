<script setup>
const {myList} = defineProps(['myList']);

const removeItem = (index) => {
  // myList = myList.slice(index);
  // myList.value = [];

  console.log(items);

}

</script>

<template>
  <ul>
    <li v-for="(item,index) in myList" :key="index">
      <input type="text" :value="myList[index]" @input="event=>$emit('modifyList',index,event.target.value)"/>
      <!--      <button @click="()=>{removeItem(index+1)}">-</button>-->
      <button @click="$emit('modifyList',index)">-</button>
    </li>
  </ul>
</template>

<style scoped>

</style>