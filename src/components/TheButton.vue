<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<style scoped>
.button {
  height: 48px;
  font-family: Merriweather, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 14px 36px;
  border: none;
  color: var(--white);
  background-color: var(--color-accent);
}
</style>
