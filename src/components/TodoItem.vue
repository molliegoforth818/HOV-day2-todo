<template>
<div>
  <h3 :class="{ completed: todo.complete }">{{ todo.name }}</h3>
  <button @click="handleClick">{{buttonText}}</button>
</div>
</template>

<script>
export default {
    props: ["todo"],

    methods: {
        handleClick() {
            this.$emit("status-change", this.todo);
        },
    },
    computed: {
        buttonText() {
            return this.todo.complete ? "Mark Incomplete" : "Mark Complete";
        },
    }
};
</script>

<style scoped>
div {
  border: 3px solid tomato;
  margin: 15px;
  padding: 10px;
}
.completed {
    text-decoration: line-through;
    text-decoration-color: seagreen;
}
</style>