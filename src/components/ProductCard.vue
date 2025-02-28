<template>
  <div
    class="product-card"
    :style="{ opacity: !price ? '.5' : '1' }"
    @click="$emit('click', id)"
  >
    <img width="280" height="160" :src="img" :alt="title" />
    <div class="product-card__content">
      <h2>{{ title }}</h2>
      <div class="product-card__action">
        <template v-if="price">
          <div class="product-card__price">
            <h6 v-if="price.old">
              <s>{{ price.old }} $</s>
            </h6>
            <h3>{{ price.current }} $</h3>
          </div>
          <TheButton @click="buttonClickHandler" :buttonState="buttonState">{{
            buttonStateLabel
          }}</TheButton>
        </template>
        <template v-else>
          <h3 class="product-card__price_soldout">Продана на аукционе</h3>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
import TheButton from "./TheButton.vue";

export default {
  components: {
    TheButton,
  },
  emits: ["click"],
  props: {
    id: Number,
    title: String,
    img: String,
    price: {
      type: [Object, null],
      required: false,
    },
  },
  data() {
    return {
      buttonState: 0,
    };
  },
  computed: {
    buttonStateLabel() {
      const stateLabels = ["Купить", "Обрабатывается", "В корзине"];
      return stateLabels[this.buttonState] || null;
    },
  },
  mounted() {
    const cart = JSON.parse(localStorage.getItem("cart") || "{}");
    this.buttonState = cart[this.id] ? 2 : 0;
  },
  methods: {
    buttonClickHandler() {
      this.buttonState = 1;

      setTimeout(() => {
        this.buttonState = 2;
        this.saveToLocalStorage();
      }, 2000);
    },
    saveToLocalStorage() {
      const cart = JSON.parse(localStorage.getItem("cart") || "{}");
      cart[this.id] = this.buttonState === 2;
      localStorage.setItem("cart", JSON.stringify(cart));
    },
  },
};
</script>

<style scoped>
.product-card {
  display: flex;
  width: 280px;
  height: 328px;
  flex-direction: column;
  border: 1px solid var(--gray);
  cursor: pointer;
}

.product-card:hover {
  border-color: var(--color-accent);
}

.product-card__content {
  display: flex;
  flex-direction: column;
  gap: 22px;
  padding: 24px 20px;
}

.product-card__action {
  display: flex;
  justify-content: space-between;
  gap: 21px;
}

.product-card__price {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}

.product-card__price_soldout {
  margin-top: 12px;
}
</style>
