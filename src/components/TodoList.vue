<template>
<div>
  <h1>ToDoList</h1>
  <h3> {{ itemsRemaining }}</h3>
  <div v-for="item in todos" :key="item.id">
    <todo-item :todo="item" @status-change="handleStatusChange" />
  </div>
  </div>
</template>

<script>
import { todoItems } from "../data";
import TodoItem from "./TodoItem";

export default {
 components: { TodoItem },
 data() {
   return{
     todos: [...todoItems]
   }
 },
methods: {
  handleStatusChange(item) {
    item.complete = !item.complete;
  }
},
computed: {
  itemsRemaining() {
    return this.todos.filter((todo) => !todo.complete);
  }
}                            
}
</script>

<style>

</style>