<template>
  <div class="header">
    <div class="container">
      <ul>
        <li>Каталог</li>
        <li>Доставка</li>
        <li>Оплата</li>
        <li>Контакты</li>
        <li>О компании</li>
      </ul>
      <div class="header__search-bar">
        <input type="text" :value="value" @input="updateValue()" placeholder="Поиск по названию картины" class="header__search-input" />
        <TheButton>Найти</TheButton>
      </div>
    </div>
  </div>
</template>

<script>
import TheButton from './TheButton.vue';

export default {
  props: {
    value: {
      type: String,
      required: true
    }
  },
  components: {
    TheButton
  },
  methods: {
    updateValue() {
      this.$emit('input', event.target.value)
    }
  }
}
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

.header ul {
  display: flex;
  padding-left: 96px;
  gap: 48px;
}

.header li {
  list-style-type: none;
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
  color: var(--gray)
}

.header__search-input:focus-visible {
  outline: none;
  border-color: var(--dark-gray);
}
</style>
