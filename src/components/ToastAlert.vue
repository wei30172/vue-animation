<template>
  <transition name="toast">
    <div v-if="showError || showSuccess" class="toast-alert-container">
      <div
        class="toast-alert"
        :class="{ error: showError, success: showSuccess }"
      >
        <slot />
      </div>
    </div>
  </transition>
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
    padding: 8px;
    border-radius: 6px;
    text-align: center;
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

@keyframes shake {
  0% {
    transform: translateY(-120px);
  }
  50% {
    transform: translateY(0);
  }
  60% {
    transform: translateX(-6px);
  }
  70% {
    transform: translateX(0px);
  }
  80% {
    transform: translateX(4px);
  }
  90% {
    transform: translateX(0px);
  }
  100% {
    transform: translateX(-2px);
  }
}

.toast-enter-active {
  animation: shake 0.4s ease;
}

.toast-leave-to {
  transform: translateY(-120px);
}
</style>
