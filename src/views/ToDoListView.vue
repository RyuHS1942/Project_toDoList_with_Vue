<script setup lang="ts">
import InsertTemplate from "../components/InsertInfo.vue"
import ViewTemplate from "../components/ViewList.vue"
import {ref} from "vue";

const todoList = ref([
  {id: 1, name: "true", checked: true, updated: false}
  , {id: 2, name: "false", checked: false, updated: false}
  , {id: 3, name: "true2", checked: true, updated: false}
  , {id: 4, name: "false2", checked: false, updated: false}
])
defineProps(['todoLists'])

</script>

<template>
  <div>
    {{todoList}}

    <insert-template :todoList="todoList" />

    <view-template :title="'ToDoList'" :todoList="todoList" :checked="false" @response="(lists) => todoList = lists" />

    <view-template :title="'DoneList'" :todoList="todoList" :checked="true" @response="(lists) => todoList = lists" />
  </div>
</template>

<style scoped>

</style>