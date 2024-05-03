<script setup>
import ListGenerator from './ListGenerator.vue';
import ToDoList from './ToDoList.vue';

const {list} = defineProps([
    'list'
]);

const emit = defineEmits(['modifyListMain'])

const modifyList_function = (index,text = null)=>{
  emit('modifyListMain',index,text)
}

console.log(list.length);


</script>

<template>
<div v-if="list.length>0">
  <ToDoList @modify-list="modifyList_function" :myList="list" />
</div>
<div v-else style="margin-top: 50px;">
    Your ToDoList is Empty 🙁
</div>


<ListGenerator :myList="list" />
<!--<ListGenerator v-if="list.length===0" :myList="list" />-->
<!--<ListGenerator v-else-if="list.length>0" v-for="list in Item" :key="Item" :myList="list" />-->

</template>

<style>

</style>