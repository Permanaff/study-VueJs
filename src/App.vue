<style scoped>
  .wrapper{
    display: flex;
    flex-direction: column;
    height: 100svh;
    justify-content: center;
    align-items: center;
  }
</style>

<template>
  <section class="wrapper">
    <FormTodo @add-todo="add" />
    <TodoList :todos="todos" @remove="remove" />
  </section>
</template>

<script setup>
import { ref } from 'vue';
import FormTodo from './components/FormTodo.vue'
import TodoList from './components/TodoList.vue'

const todos = ref([]);

function add (data) {
  todos.value.push({id:crypto.randomUUID(), todo:data.todo})
  data.clear();
}

function remove(id) {
 todos.value = todos.value.filter(item => item.id !== id)
}

</script>

