<template>
  <div class="sales-card">
    <img width="280" height="160" src="../assets/painting-1.png" alt="">
    <div class="sales-card__content">
      <h2>«Рождение Венеры» Сандро Боттичелли</h2>
      <div class="sales-card__action">
        <div class="sales-card__price">
          <h6><s>6 000 000 $</s></h6>
          <h3>1 000 000 $</h3>
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
}
</style>
