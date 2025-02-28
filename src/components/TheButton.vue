<template>
  <button
    @click.stop="$emit('click')"
    class="button"
    :class="{
      'button-in-progress': buttonState === 1,
      'button-in-the-cart': buttonState === 2,
    }"
  >
    <simple-spinner
      v-if="buttonState === 1"
      size="20"
      line-fg-color="#C1B4B1"
    ></simple-spinner>
    <IconDone v-if="buttonState === 2"></IconDone>

    <slot></slot>
  </button>
</template>

<script>
import IconDone from "./icons/IconDone.vue";
import SimpleSpinner from "vue-simple-spinner";

export default {
  components: {
    IconDone,
    SimpleSpinner,
  },
  emits: ["click"],
  props: {
    buttonState: Number,
  },
};
</script>

<style scoped>
.button {
  width: 118px;
  height: 48px;
  font-family: Merriweather, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: var(--color-accent);
  padding: 14px 36px;
  border: none;
  color: var(--white);
  cursor: pointer;
}

.button-in-progress {
  display: flex;
  flex-wrap: nowrap;
  align-items: center;
  justify-content: center;
  font-size: 10px;
  gap: 4px;
}

.button-in-the-cart {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--color-button-in-the-cart);
  padding: 14px 8px;
}

.button:hover {
  background-color: var(--color-button-hover);
}

.button:disabled {
  background-color: var(--color-button-disabled);
}
</style>
