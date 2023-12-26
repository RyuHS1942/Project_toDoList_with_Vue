<script setup lang="ts">
import {ref} from "vue";

let inputInfo = ref("");
const props = defineProps({
  todoList: Array
})
const count = props.todoList?.length + 1;

const vFocus = {
  mounted: (el) => el.focus()
}

function fnInsertInfo() {
  const newInfo = {id: count, name: inputInfo.value, checked: false, updated: false};

  if(inputInfo.value) props.todoList.push(newInfo);
  else alert("Input Info!")

  inputInfo.value = ""
}
</script>

<template>
  <h1><span>● </span>Insert Info</h1>
  <input type="text" v-model="inputInfo" v-focus />
  <button @click="fnInsertInfo">Insert</button>
</template>

<style scoped>

</style>