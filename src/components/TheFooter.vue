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
      <div class="footer__contacts">
        <div>
          <IconCalls></IconCalls>
          +7 (812) 555-55-55
        </div>
        <div>
          <IconAddress></IconAddress>
          г. Санкт-Петербург, ул. Ефимова, 3
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import IconAddress from './icons/IconAddress.vue';
import IconCalls from './icons/IconCalls.vue';

export default {
  components: {
    IconAddress,
    IconCalls
  }
}
</script>

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

.footer__contacts {
  display: flex;
  gap: 51px;
}

.footer__contacts div {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}
</style>
