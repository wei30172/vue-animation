<template>
  <ul v-if="todos.length > 0">
    <li v-for="todo in todos" :key="todo.id" class="todo">
      <span>{{ todo.todo }}</span>
      <Delete
        @click="$emit('remove-todo', todo)"
        class="delete-icon cursor-pointer"
      />
    </li>
  </ul>
  <p v-else>You completed all your todos!</p>
</template>

<script setup>
import Delete from "@/features/icons/Delete";
import { defineProps } from "vue";

defineProps({
  todos: Array,
});
</script>

<style lang="scss" scoped>
@use "../styles/mixin/colors" as colors;

ul {
  margin-top: 24px;
  position: relative;
  .todo {
    width: 100%;
    padding: 12px 6px;
    display: flex;
    align-items: center;
    background-color: colors.$white;
    color: colors.$text-primary;
    margin-bottom: 20px;
    span {
      flex: 1;
    }
    .delete-icon {
      width: 40px;
      height: 40px;
      margin-right: 8px;
      color: colors.$text-primary;
    }
  }
}
p {
  margin-top: 24px;
  text-align: center;
}
</style>
