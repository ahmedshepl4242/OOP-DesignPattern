<script setup>
import { uid } from "uid";
import { ref } from "vue";
import TodoCreater from "../components/TodoCreater.vue";
const todoList = ref([]);
const createTo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isComlemted: null,
    isEditing: null,
  });
};
</script>

<template>
  <main>
    <h1>Create Todos</h1>
    <TodoCreater @create_todo="createTo" />
  </main>
</template>
<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;

  h1 {
    margin-bottom: 16px;
    text-align: center;
  }
}
</style>
