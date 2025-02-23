<template>
  <div class="sales-card">
    <img width="280" height="160" src="../assets/painting-1.png" alt="">
    <div>
      <h2>«Рождение Венеры» Сандро Боттичелли</h2>
      <div class="sales-card__action">
        <div class="sales-card__price">
          <h6><s>6 000 000 $</s></h6>
          <h3>3 000 000 $</h3>
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
}

.sales-card__action {
  display: flex;
}
</style>
