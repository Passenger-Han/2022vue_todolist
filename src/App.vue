<template>
  <div class="head">
    <h1>TODO LIST</h1>
  </div>
  <todo-input v-on:addTodo="addTodoItem"></todo-input>
  <todolist :todoItem="todoItem" @remove="removeItem"></todolist>
  <todofooter @removeAll="removeAllItems"></todofooter>
</template>

<script>
import '@/assets/initial.css'

import TodoInput from '@/components/todoInput.vue';
import Todolist from '@/components/todolist.vue';
import Todofooter from '@/components/todofooter.vue';

export default {
  components: {
    TodoInput,
    Todolist,
    Todofooter
  },

  data(){
    return {
      todoItem: [],
    }
  },

  created(){
    for (let i = 0; i < localStorage.length; i++){
      this.todoItem.push(localStorage.key(i));
    };
  },

  methods: {
    addTodoItem: function(item){
      this.todoItem.push(item);
      localStorage.setItem(item, item);
    },

    removeItem: function(index, item){
      console.log(index, item);
      this.todoItem.splice(index, 1);
      localStorage.removeItem(item);
    },

    removeAllItems: function(){
      localStorage.clear();
      this.todoItem = [];
    },
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

body {font-family: 'Roboto', sans-serif; background: black;}
#app {width: 100%; margin: 0 auto; padding: 24px; background: white;}
.head {
  margin-bottom: 8px;
}

</style>