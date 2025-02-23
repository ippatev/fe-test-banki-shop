<template>
  <footer class="footer">
  <div class="container">
    <ul>
      <li>Каталог</li>
      <li>Доставка</li>
      <li>Оплата</li>
      <li>Контакты</li>
      <li>О компании</li>
    </ul>
    <div class="footer__contacts"></div>
  </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: var(--color-footer);
  margin-top: auto;
}

.footer .container {
  height: 97px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: nowrap;
}

.footer ul {
  display: flex;
  padding-left: 96px;
  gap: 48px;
}

.footer li {
  list-style-type: none;
}
</style>
