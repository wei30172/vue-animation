<template>
  <div class="view">
    <ToastAlert :showError="showError" :showSuccess="showSuccess">
      <p v-show="showError">Cannot be empty!</p>
      <p v-show="showSuccess">Add successfully!</p>
    </ToastAlert>
    <div class="view-header">
      <h1>Add Todo</h1>
    </div>
    <AddTodo @add-todo="addTodo" @error-todo="errorTodo" />
    <TodosList :todos="todos" @remove-todo="removeTodo" />
  </div>
</template>

<script setup>
import { uid } from "uid";
import { ref } from "vue";
import AddTodo from "@/components/AddTodo.vue";
import TodosList from "@/components/TodosList.vue";
import ToastAlert from "@/components/ToastAlert.vue";

const todos = ref([
  { todo: "delectus aut autem", id: uid() },
  { todo: "quis ut nam facilis et officia qui", id: uid() },
  { todo: "fugiat veniam minus", id: uid() },
]);

const addTodo = (payload) => {
  todos.value.unshift({
    todo: payload,
    id: uid(),
  });
  successTodo();
};

const showError = ref(false);
const showSuccess = ref(false);

const errorTodo = () => {
  showSuccess.value = false;
  showError.value = true;
  setTimeout(() => {
    showError.value = false;
  }, 3000);
};

const successTodo = () => {
  showError.value = false;
  showSuccess.value = true;
  setTimeout(() => {
    showSuccess.value = false;
  }, 3000);
};

const removeTodo = (payload) => {
  todos.value = todos.value.filter((todo) => todo.id !== payload.id);
};
</script>

<style lang="scss" scoped>
.view {
  max-width: 360px;
  margin: 0 auto;
  padding: 20px 12px;
  .view-header {
    margin-bottom: 32px;
  }
}
</style>
