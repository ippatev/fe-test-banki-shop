<template>
  <div class="sales-card">
    <img width="280" height="160" :src="img" :alt="title">
    <div class="sales-card__content">
      <h2>{{ title }}</h2>
      <div class="sales-card__action">
        <div class="sales-card__price">
          <h6 v-if="price.old"><s>{{price.old}} $</s></h6>
          <h3>{{price.current}} $</h3>
        </div>
        <TheButton>Купить</TheButton>
      </div>
    </div>
  </div>
</template>

<script>
import TheButton from './TheButton.vue';

export default {
  components: {
    TheButton
  },
  props: {
    title: String,
    img: String,
    price: Object
  }
}
</script>

<style scoped>
.sales-card {
  display: flex;
  width: 280px;
  height: 328px;
  flex-direction: column;
  border: 1px solid var(--gray);
}

.sales-card__content {
  display: flex;
  flex-direction: column;
  gap: 22px;
  padding: 24px 20px;
}

.sales-card__action {
  display: flex;
  gap: 21px;
}

.sales-card__price {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}
</style>
