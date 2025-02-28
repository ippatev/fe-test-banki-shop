<template>
  <div id="app">
    <TheHeader v-model="searchQuery"></TheHeader>

    <main class="main-content container">
      <header>
        <h1>Картины эпохи Возрождения</h1>
      </header>

      <div class="product-list">
        <ProductCard
          v-for="card in filteredProductCards"
          :key="card.id"
          :id="card.id"
          :title="card.title"
          :img="card.img"
          :price="card.price"
        >
        </ProductCard>
      </div>

      <ProductModal
        v-if="0"
        :id="0"
        title="Product Title"
        description="Product Description"
        img="https://example.com/image.jpg"
        :price="{ current: 1_000_000, old: null }"
        @close="() => {}"
      ></ProductModal>
    </main>

    <TheFooter></TheFooter>
  </div>
</template>

<script>
import ProductCard from "./components/ProductCard.vue";
import ProductModal from "./components/ProductModal.vue";
import TheFooter from "./components/TheFooter.vue";
import TheHeader from "./components/TheHeader.vue";

export default {
  name: "App",
  components: {
    TheHeader,
    TheFooter,
    ProductCard,
    ProductModal,
  },
  data() {
    return {
      productCards: [],
      searchQuery: "",
    };
  },
  created() {
    const productImgNames = [
      "painting-1.png",
      "painting-2.png",
      "painting-3.png",
      "painting-4.png",
    ];

    this.productCards = [
      {
        id: 0,
        title: "«Рождение Венеры» Сандро Боттичелли",
        img: require(`@/assets/${productImgNames[0]}`),
        price: {
          current: 1_000_000,
          old: 2_000_000,
        },
      },
      {
        id: 1,
        title: "«Тайная вечеря»  Леонардо да Винчи",
        img: require(`@/assets/${productImgNames[1]}`),
        price: {
          current: 3_000_000,
          old: null,
        },
      },
      {
        id: 2,
        title: "«Сотворение Адама» Микеланджело",
        img: require(`@/assets/${productImgNames[2]}`),
        price: {
          current: 5_000_000,
          old: 6_000_000,
        },
      },
      {
        id: 3,
        title: "«Урок анатомии»  Рембрандт",
        img: require(`@/assets/${productImgNames[3]}`),
        price: null,
      },
    ];
  },
  computed: {
    filteredProductCards: function () {
      return this.productCards.filter((card) => {
        return card.title
          .toLowerCase()
          .includes(this.searchQuery.toLowerCase());
      });
    },
  },
};
</script>

<style>
:root {
  --white: #fff;
  --black: #343030;
  --gray: #e1e1e1;
  --dark-gray: ##b5b5b5;
  --color-accent: #403432;
  --color-footer: #eceaea;
  --color-button-hover: #776763;
  --color-button-disabled: #c1b4b1;
  --color-button-in-the-cart: #5b3a32;
}

body {
  margin: 0;
  padding: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Merriweather, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--black);
  font-size: 14px;
}

h1 {
  font-size: 24px;
  font-weight: bold;
}

h2 {
  font-size: 18px;
  font-weight: normal;
}

h3 {
  font-size: 16px;
  font-weight: bold;
}

h4,
h5,
h6 {
  font-size: 14px;
}

h4 {
  font-weight: bold;
}

h5 {
  font-weight: bold;
}

h6 {
  font-weight: lighter;
}

.container {
  max-width: 1216px;
  margin: 0 auto;
}

.main-content {
  min-height: 100vh;
  margin-top: 45px;
}

.product-list {
  display: flex;
  flex-direction: row;
  gap: 32px;
  margin-top: 40px;
}
</style>
