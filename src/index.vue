<template>
  <div class="fake-card" :class="shadow ? 'is-' + shadow + '-shadow' : 'is-always-shadow'">
    <div v-if="$slots.header || header" class="fake-card__header">
      <slot name="header">{{ header }}</slot>
    </div>
    <div class="fake-card__body">
      <slot></slot>
    </div>
    <div v-if="$slots.footer || footer" class="fake-card__footer">
      <slot name="footer">{{ footer }}</slot>
    </div>
  </div>
</template>
<script lang="ts" setup>
defineProps({
  // header slot
  header: {
    type: String,
    default: '',
  },
  // footer slot
  footer: {
    type: String,
    default: ''
  },
  // box-shadow
  shadow: {
    type: String,
    default: '',
  }
})
</script>
<style>
/* Copy from element-plus / card */
.is-always-shadow {
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
}
.is-hover-shadow:hover {
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
}
.is-never-shadow {
  box-shadow: none;
}
.fake-card {
  --fake-text-color-primary: #303133;
  --fake-transition-duration: 0.3s;
  --fake-card-border-color: #ebeef5;
  --fake-card-border-radius: 4px;
  --fake-card-padding: 20px;
  --fake-card-bg-color: #fff;
}
.fake-card {
  border-radius: var(--fake-card-border-radius);
  border: 1px solid var(--fake-card-border-color);
  background-color: var(--fake-card-bg-color);
  overflow: hidden;
  color: var(--fake-text-color-primary);
  transition: var(--fake-transition-duration);
}
.fake-card__header {
  padding: calc(var(--fake-card-padding) - 2px) var(--fake-card-padding);
  border-bottom: 1px solid var(--fake-card-border-color);
  box-sizing: border-box;
}
.fake-card__body {
  padding: var(--fake-card-padding);
}
.fake-card__footer {
  padding: calc(var(--fake-card-padding) - 2px) var(--fake-card-padding);
  border-top: 1px solid var(--fake-card-border-color);
  box-sizing: border-box;
}
</style>