<script setup>
import {ref, onMounted} from 'vue'
import Lists from './components/Lists.vue';

let ListStorage = localStorage.getItem('lists');
const myList = ref([]);

if (ListStorage == null) {
  localStorage.setItem('lists', JSON.stringify([]));
  myList.value = [];
} else {
  if (JSON.parse(ListStorage).length > 0) {
    myList.value = JSON.parse(ListStorage);
  } else {
    myList.value = [];
  }
}


const modifyList = (index, text = null) => {
  if (text == null) {
    myList.value.splice(index, 1);
  } else {
    myList.value[index] = text;
  }
  localStorage.setItem('lists', JSON.stringify(myList.value));
}

onMounted(() => {

});

</script>

<template>

  <div class="container">

    <h1>ToDo List</h1>
    <Lists @modify-list-main="modifyList" :list="myList"/>


  </div>

</template>

<style scoped>
</style>
