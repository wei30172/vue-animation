<template>
  <div v-if="showError || showSuccess" class="toast-alert-container">
    <div
      class="toast-alert"
      :class="{ error: showError, success: showSuccess }"
    >
      <slot />
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  showError: Boolean,
  showSuccess: Boolean,
});
</script>

<style lang="scss" scoped>
@use "../styles/mixin/colors" as colors;

.toast-alert-container {
  position: relative;
  .toast-alert {
    width: 100%;
    position: absolute;
    padding: 16px;
    border-radius: 6px;
    color: colors.$white;
    background-color: colors.$secondary;
    &.error {
      background-color: colors.$danger-primary;
    }
    &.success {
      background-color: colors.$success-primary;
    }
  }
}
</style>
