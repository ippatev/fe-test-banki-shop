<template>
  <button
    class="button button-accent"
    :class="{ 'button-secondary': inTheCart }"
  >
    <template v-if="inTheCart">
      <IconDone></IconDone>
      В корзине
    </template>
    <template v-else>
      <slot></slot>
    </template>
  </button>
</template>

<script>
import IconDone from "./icons/IconDone.vue";

export default {
  components: {
    IconDone,
  },
  props: {
    inTheCart: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  data() {
    return {
      progressStatus: null,
    };
  },
};
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
  cursor: pointer;
}

.button-accent {
  background-color: var(--color-accent);
}

.button-secondary {
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
