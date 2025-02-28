<template>
  <div class="modal-overlay" @click.self="close">
    <div class="modal-content">
      <button class="close-btn" @click="close">×</button>
      <div class="slider">
        <img :src="currentImage" alt="Product image" class="slide" />
        <div class="slider-controls">
          <button @click="prevSlide">‹</button>
          <button @click="nextSlide">›</button>
        </div>
      </div>
      <h2>{{ title }}</h2>
      <p>{{ description }}</p>
      <p class="price">{{ price.current }} $</p>
    </div>
  </div>
</template>

<script>
const productImgNames = [
  "painting-1.png",
  "painting-2.png",
  "painting-3.png",
  "painting-4.png",
];
export default {
  props: {
    id: Number,
    title: String,
    description: String,
    images: {
      type: Array,
      required: false,
      default: () => [
        require(`@/assets/${productImgNames[0]}`),
        require(`@/assets/${productImgNames[1]}`),
        require(`@/assets/${productImgNames[2]}`),
        require(`@/assets/${productImgNames[3]}`),
      ],
    },
    price: {
      type: [Object, null],
      required: false,
    },
  },
  emits: ["close"],
  data() {
    return {
      currentSlide: 0,
    };
  },
  computed: {
    currentImage() {
      return this.images[this.currentSlide];
    },
  },
  created() {
    this.currentSlide = this.id;
  },
  methods: {
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.images.length;
    },
    prevSlide() {
      this.currentSlide =
        (this.currentSlide - 1 + this.images.length) % this.images.length;
    },
    close() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  animation: fadeIn 0.3s ease-out;
  overflow-y: auto;
  padding: 20px;
  @media (max-width: 480px) {
    padding: 10px;
    align-items: flex-start;
  }
  @supports (backdrop-filter: blur(2px)) {
    backdrop-filter: blur(2px);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.modal-content {
  position: relative;
  background: white;
  border-radius: 8px;
  padding: 30px;
  max-width: 90%;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);

  @media (max-width: 480px) {
    padding: 20px;
    width: 100%;
    border-radius: 0;
    margin-top: 20px;
  }
}
</style>
