<template>
  <div>
    <h1><span>● </span>{{ title }}</h1>
    <h3 v-for="(todoInfo) in list.filter(todoInfo => todoInfo.checked == checked)" :key="todoInfo.id">
      <input type="checkbox" v-model="todoInfo.checked"/>
      <button @click="fnUpdateInfo(list, todoInfo, inputText, todoInfo.id)">Update</button>
      <button @click="fnDeleteInfo(list, todoInfo.id)">Delete</button>

      <p class="name" @click="fnClickInfo"><span>- </span>{{ todoInfo.name }}</p>
      <input type="text" class="IName" :value="todoInfo.name"
             @input="inputText = $event.target.value"
             @blur="fnFocusOut($event, todoInfo.name)"/>
    </h3>
  </div>
</template>

<script>

export default {
  name: 'ToDoList'
  , props: {
    title: String
    , list: Array
    , checked: Boolean
  }
  , methods: {
    /*
    * update
    */
    fnUpdateInfo(list, info, inputText, id) {
      if (!inputText) inputText = info.name;

      list.find((info) => {
        info.id == id ? info.name = inputText : info.name
      });

      inputText = "";
    }
    /*
    * delete
    */
    , fnDeleteInfo(list, id) {
        list = list.filter((info) => info.id != id);
    }
  }
}

/*
  * click
  */
function fnClickInfo(event) {
  event.target.style.display = 'none';
  event.target.nextSibling.style.display = 'block';

  event.target.nextSibling.focus();
}

/*
* Focusout
*/
function fnFocusOut(event, name) {
  event.target.style.display = 'none';
  event.target.previousSibling.style.display = 'block';

  event.target.value = name;
}

</script>

<style scoped>
.name {
  margin-left: 5px;
  width: 120px;
}

.IName {
  /*display: none*/
}

input[type="text"] {
  margin-left: 5px;
  width: 120px;
}

button {
  margin-left: 5px;
}
</style>