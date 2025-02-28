<template>
  <div class="header">
    <div class="container">
      <ul class="header__nav">
        <li v-for="link in links" :key="link" class="header__link">
          <a :href="`#${link}`">{{ link }}</a>
        </li>
      </ul>
      <div class="header__search-bar">
        <input
          type="text"
          :value="value"
          @input="updateValue()"
          placeholder="Поиск по названию картины"
          class="header__search-input"
        />
        <TheButton>Найти</TheButton>
      </div>
    </div>
  </div>
</template>

<script>
import TheButton from "./TheButton.vue";

export default {
  props: {
    value: {
      type: String,
      required: true,
    },
  },
  components: {
    TheButton,
  },
  data() {
    return {
      links: ["Каталог", "Доставка", "Оплата", "Контакты", "О компании"],
    };
  },
  methods: {
    updateValue() {
      this.$emit("input", event.target.value);
    },
  },
};
</script>

<style scoped>
.header {
  border-bottom: 1px solid var(--gray);
}

.header .container {
  height: 97px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: nowrap;
}

.header__nav {
  display: flex;
  padding-left: 96px;
  gap: 48px;
}

.header__link {
  list-style-type: none;
}

.header__link a {
  text-decoration: none;
  color: var(--black);
  font-size: 16px;
  transition: color 0.2s;
}

.header__link a:hover {
  color: var(--dark-gray);
}

.header__search-input {
  width: 294px;
  height: 48px;
  padding: 14px 16px;
  border: 1px solid var(--gray);
  font-family: Merriweather, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.header__search-input::placeholder {
  color: var(--gray);
}

.header__search-input:focus-visible {
  outline: none;
  border-color: var(--dark-gray);
}

@media (max-width: 768px) {
  .header .container {
    flex-wrap: wrap;
    padding: 34px;
    height: 100%;
    gap: 20px;
  }
  .header__nav {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 20px;
  }

  .header__search-bar {
    display: flex;
    flex-direction: row;
  }

  .header__content {
    gap: 15px;
    padding: 0 15px;
  }

  .header__search-input {
    width: 160px;
  }
}

@media (max-width: 480px) {
  .search {
    flex-grow: 1;
  }

  .header__search-input {
    width: 100%;
  }

  .header__right {
    margin-left: auto;
  }
}

@media (max-width: 360px) {
  .header__content {
    padding: 0 10px;
    gap: 10px;
  }

  .header__search-input {
    padding: 6px 10px;
    font-size: 14px;
  }
}
</style>
