<template>
  <div class="header">
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
</template>

<script>
export default {}
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: nowrap;
}

.header ul {
  display: flex;
  gap: 48px;
}
</style>
