<template>
  <div class="head">
    <h1>TODO LIST</h1>
  </div>
  <todo-input v-on:addTodo="addTodoItem"></todo-input>
  <todolist :todoItem="todoItem"></todolist>
  <todofooter></todofooter>
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

  methods: {
    addTodoItem: function(item){
      this.todoItem.push(item);
    },
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

body {font-family: 'Roboto', sans-serif; background: black;}
#app {width: 400px; margin: 0 auto; padding: 24px; background: white;}
.head {
  margin-bottom: 8px;
}

</style>