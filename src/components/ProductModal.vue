<template>
  <div class="modal-overlay" @click.self="close">
    <div class="modal-content">
      <button class="close-button" @click="close">×</button>
      <div class="slider">
        <img :src="currentImage" :alt="title" class="modal-image" />
        <div class="slider-controls">
          <button class="slider-button prev" @click="prevSlide">‹</button>
          <button class="slider-button next" @click="nextSlide">›</button>
        </div>
      </div>
      <h2 class="modal-title">{{ title }}</h2>
      <p class="modal-description">{{ description }}</p>
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
    description: {
      type: String,
      required: false,
      default:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas faucibus placerat arcu nec vulputate. Fusce blandit mauris ut mauris egestas varius. Suspendisse potenti. Orci varius.",
    },
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
  display: flex;
  justify-content: center;
  align-items: center;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 20px;
  z-index: 1000;
  animation: fadeIn 0.3s ease-out;
  overflow-y: auto;
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
  max-width: 50%;
  background: white;
  padding: 30px;
  border-radius: 8px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);

  @media (max-width: 480px) {
    width: 100%;
    margin-top: 20px;
    padding: 20px;
    border-radius: 0;
  }
}

.close-button {
  position: absolute;
  top: 10px;
  right: 15px;
  font-size: 24px;
  cursor: pointer;
  color: #333;
}

.close-button:hover {
  color: #000;
}

.modal-image {
  max-width: 100%;
  height: auto;
  border-radius: 8px;
  margin-bottom: 15px;
}

.modal-title {
  font-size: 24px;
  margin-bottom: 10px;
}

.modal-description {
  font-size: 16px;
  color: #555;
}

.slider {
  position: relative;
  display: inline-block;
}

.slider-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  font-size: 24px;
  cursor: pointer;
  padding: 10px;
  border-radius: 50%;
  z-index: 1001;
}

.slider-button.prev {
  left: 10px;
}

.slider-button.next {
  right: 10px;
}

.slider-button:hover {
  background-color: rgba(0, 0, 0, 0.8);
}
</style>
