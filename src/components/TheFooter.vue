<template>
  <footer class="footer">
    <div class="container">
      <ul class="footer__nav">
        <li v-for="link in links" :key="link" class="footer__link">
          <a :href="`#${link}`">{{ link }}</a>
        </li>
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
import IconAddress from "./icons/IconAddress.vue";
import IconCalls from "./icons/IconCalls.vue";

export default {
  components: {
    IconAddress,
    IconCalls,
  },
  data() {
    return {
      links: ["Каталог", "Доставка", "Оплата", "Контакты", "О компании"],
    };
  },
};
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

.footer__nav {
  display: flex;
  padding-left: 96px;
  gap: 48px;
}

.footer__link {
  list-style-type: none;
}

.footer__link a {
  text-decoration: none;
  color: var(--black);
  font-size: 16px;
  transition: color 0.2s;
}

.footer__link a:hover {
  color: var(--dark-gray);
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

@media (max-width: 768px) {
  .footer .container {
    padding: 34px;
    height: 100%;
  }
  .footer__nav,
  .footer__contacts {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .footer__content {
    gap: 15px;
    padding: 0 15px;
  }
}

@media (max-width: 480px) {
  .footer__right {
    margin-left: auto;
  }
}

@media (max-width: 360px) {
  .footer__content {
    padding: 0 10px;
    gap: 10px;
  }
}
</style>
