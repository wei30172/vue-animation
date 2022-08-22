<template>
  <div class="add-todo box-shadow">
    <input
      type="text"
      placeholder="New todo"
      v-model="newTodo"
      @keyup.enter="handleAddTodo"
    />
  </div>
</template>

<script setup>
import { ref, defineEmits } from "vue";
const emit = defineEmits(["add-todo", "error-todo"]);
const newTodo = ref("");

const handleAddTodo = () => {
  if (newTodo.value !== "") {
    emit("add-todo", newTodo.value);
    newTodo.value = "";
    return;
  }
  emit("error-todo");
};
</script>

<style lang="scss" scoped>
.add-todo {
  input[type="text"] {
    border: 1px solid transparent;
    border-radius: 6px;
    padding: 18px 12px;
    width: 100%;
  }
}
</style>
