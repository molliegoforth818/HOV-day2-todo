<template>
<div>
  <h1>ToDoList</h1>
  <h3> {{ itemsRemainingMessage }}</h3>
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
  itemsRemainingMessage() {
    const remaining = this.todos.filter((todo) => !todo.complete).length;
    if (remaining == 1) {
      return "There is 1 item left to do today"
    }
    return `There are ${remaining} items let to do today`
  }
}                            
}
</script>

<style>

</style>