<template>
  <div id="app">
    <TheHeader v-model="searchQuery"></TheHeader>

    <main class="main-content container">
      <header>
        <h1>Картины эпохи Возрождения</h1>
      </header>

      <div class="sales-list">
        <SalesCard
          v-for="card in filteredSalesCard"
          :key="card.id"
          :title="card.title"
          :img="card.img"
          :price="card.price">
        </SalesCard>
      </div>
    </main>

    <TheFooter></TheFooter>
  </div>
</template>

<script>
import SalesCard from './components/SalesCard.vue';
import TheFooter from './components/TheFooter.vue';
import TheHeader from './components/TheHeader.vue';

export default {
  name: 'App',
  components: {
    TheHeader,
    SalesCard,
    TheFooter
  },
  data() {
    return {
      salesCards: [],
      searchQuery: ''
    }
  },
  created() {
    const salesImgNames = ['painting-1.png', 'painting-2.png', 'painting-3.png']

    this.salesCards = [
      {
        id: 0,
        title: '«Рождение Венеры» Сандро Боттичелли',
        img: require(`@/assets/${salesImgNames[0]}`),
        price: {
          current: 1_000_000,
          old: 2_000_000
        }
      },
      {
        id: 1,
        title: '«Тайная вечеря»  Леонардо да Винчи',
        img: require(`@/assets/${salesImgNames[1]}`),
        price: {
          current: 3_000_000,
          old: null
        }
      },
      {
        id: 2,
        title: '«Сотворение Адама» Микеланджело',
        img: require(`@/assets/${salesImgNames[2]}`),
        price: {
          current: 5_000_000,
          old: null
        }
      }
    ]
  },
  computed: {
    filteredSalesCard: function() {
      return this.salesCards.filter((card) => {
        return card.title.toLowerCase().includes(this.searchQuery.toLowerCase());
      })
    }
  }
}
</script>

<style>
:root {
  --white: #fff;
  --black: #343030;
  --gray: #E1E1E1;
  --dark-gray: ##B5B5B5;
  --color-accent: #403432;
  --color-footer: #ECEAEA;
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

.sales-list {
  display: flex;
  flex-direction: row;
  gap: 32px;
  margin-top: 40px;
}
</style>
