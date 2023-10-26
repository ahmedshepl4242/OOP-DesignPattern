<script setup>
import { reactive, ref, defineEmits } from "vue";

const emit = defineEmits(["create_todo"]);
const todo = ref("");

const todoState = reactive({
  todo: "",
  invalid: false,
  errMsg: "",
});

// const CreatTodo = () => {};
const CreateTodo = () => {
  todoState.invalid = null;
  if (todoState.todo !== "") {
    emit("create_todo", todoState.todo);
    todoState.todo = "";
    return;
  }
  todoState.invalid = true;
  todoState.errMsg = "todo value cant be empty";
};
</script>
<template>
  <div class="input-todo" :class="{ 'inp-err': todoState.invalid }">
    <input type="text" v-model="todoState.todo" />
    <button @click="CreateTodo()">Create</button>
  </div>
  <p v-if="todoState.invalid" class="err_Msg">{{ todoState.errMsg }}</p>
  <!-- <p v-show="todoState.invalid" class="err_msg">{{ todoState.errMsg }}</p> -->
</template>

<style lang="scss" scoped>
.input-todo {
  display: flex;
  //   transition: 250ms ease;
  border: 2px solid #41b080;
  border-radius: 5px;
  &:inp-err {
    border: 20px solid red;
    border-color: rgb(206, 51, 51);
    // border-block: 20px;
  }

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;

    &:focus {
      outline: none;
    }
  }

  button {
    padding: 8px 16px;
    border: none;
  }
}
.err_Msg {
  // font-family;

  color: red;
  font-size: 14px;
  margin-top: 2px;
  .input-todo {
    border: red;
  }
  // margin-left: 20px;
  // align-items: center;
  display: flex;
  justify-content: center;
  font-family: serif;
}
.input-todo {
  margin-top: 20px;
  margin-left: 20px;
  margin-right: 20px;
  // margin-bottom: 20px;
  padding: 5px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  background-color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  input {
    flex: 1;
    // padding: 10px;
    border: none;
    outline: none;
    font-size: 18px;
  }
  button {
    // padding: 10px 20px;
    border: none;
    outline: none;
    background-color: #41b080;
    color: #fff;
    font-size: 18px;
    border-radius: 5px;
    cursor: pointer;
  }
}
</style>
