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
        <input type="text" value="" placeholder="Поиск по названию картины" class="header__search-input" />
        <button class="header__search-button">Найти</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
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

.header__search-input,
.header__search-button {
  height: 48px;
  font-family: Merriweather, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.header__search-input {
  padding: 14px 16px;
  border: 1px solid var(--gray)
}

.header__search-input::placeholder {
  color: var(--gray)
}

.header__search-button {
  padding: 14px 36px;
  border: none;
  color: var(--white);
  background-color: var(--color-accent);
}
</style>
