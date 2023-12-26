<script setup lang="ts">
import {computed, ref} from "vue";

const props = defineProps({
  title: String
  , todoList: Array
  , checked: Boolean
})
const emit = defineEmits(['response']);

const todoList = computed({
  get: () => props.todoList,
  set: (val) => emit('response', val)
})

let inputText = "";

const vFocus = {
  mounted: (el) => el.focus()
}

function fnUpdateInfo(info) {
  if(info.updated === true) info.name = inputText;
  else inputText = info.name;

  info.updated = !info.updated;
}

function fnRollbackInfo(info) {
  info.updated = !info.updated;
}

function fnDeleteInfo(id) {
  todoList.value = todoList.value.filter(todoInfo => todoInfo.id != id);
}
</script>

<template>
  <h1><span>● </span>{{ props.title }}</h1>
  <h3 v-for="(todoInfo) in todoList.filter(todoInfo => todoInfo.checked == props.checked)" :key="todoInfo.id">
    <input type="checkbox" v-model="todoInfo.checked" />
    <h3 v-if="todoInfo.updated === false">
      {{todoInfo.name}}
    </h3>
    <h3 v-else>
      <input type="text" :value="todoInfo.name" v-focus
             @input="inputText = $event.target.value"/>
      <button @click="fnRollbackInfo(todoInfo)">Rollback</button>
    </h3>
    <button @click="fnUpdateInfo(todoInfo)">Update</button>
    <button @click="fnDeleteInfo(todoInfo.id)">Delete</button>
  </h3>
</template>

<style scoped>

</style>