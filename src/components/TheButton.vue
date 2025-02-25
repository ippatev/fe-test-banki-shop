<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    inTheCart: {
      type: Boolean,
      required: false,
      default: false
    }
  }
}
</script>

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
  cursor: pointer;
}

.button:hover {
  background-color: var(--color-button-hover);
}

.button:disabled {
  background-color: var(--color-button-disabled);
}

.button_in-the-cart {
  background-color: var(--color-button-in-the-cart);
}
</style>
