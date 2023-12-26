<template>
  <div>
    <h1><span>● </span>{{ title }}</h1>
    <input class="input" type="text" v-model="inputName">
    <button @click="fnInsertInfo(list, count, {inputName})">Make</button>
  </div>
</template>

<script>
export default {
  name: 'insertInfo'
  , props: {
    title: String
    , list: Array
    , count: Number
  }
  , methods: {
    /*
    * insert
    */
    fnInsertInfo(list, count, inputName) {
      if (inputName) {
        const newInfo = {id: count, name: inputName.inputName, checked: false};
        list.push(newInfo);
        inputName = "";
      } else alert("내용을 입력하시오.");
    }
  }
}
</script>

<style scoped>

input[type="text"] {
  margin-left: 5px;
  width: 120px;
}

button {
  margin-left: 5px;
}
</style>