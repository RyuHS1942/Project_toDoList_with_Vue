<template>
  <div>
    <div class="content">
      <h1><span>● </span>현재 메모리 데이터</h1>
      {{ todoList }}
    </div>

    <div class="content">
      <insertInfo :title="'추가할 일'" :list="todoList" :count="count"/>
    </div>

    <div class="content">
      <toDoList :title="'해야할 일'" :list="todoList" :checked="true"/>
    </div>

    <div class="content">
      <toDoList :title="'완료한 일'" :list="todoList" :checked="false"/>
    </div>
  </div>
</template>

<script setup lang="ts">
import toDoList from "@/components/ListComponent.vue";
import insertInfo from "@/components/InsertComponent.vue"

import {ref} from "vue";

const todoList = ref([
  {id: 1, name: "true", checked: true}
  , {id: 2, name: "true2", checked: true}
  , {id: 3, name: "false", checked: false}
  , {id: 4, name: "false2", checked: false}
]);

let count = todoList.value.length + 1;

</script>

<style scoped>
.content {
  margin-bottom: 20px;
}
</style>