<template>
  <div :class="['card', cardClass]">
    <div class="card-content">
      <div class="card-title">{{ title }}</div>
      <div class="card-details">
        <div class="card-icon">
          <img :src="iconPath" alt="Card Icon" />
        </div>
        <div class="card-number">{{ number }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardComponent",
  props: {
    title: {
      type: String,
      required: true,
    },
    number: {
      type: [String, Number],
      required: true,
    },
    icon: {
      type: String,
      required: true,
    },
    cardClass: {
      type: String,
      default: "",
    },
  },
  computed: {
    iconPath() {
      return require(`@/assets/icons/${this.icon}`);
    },
  },
};
</script>

<style scoped>
.card {
  display: flex;
  align-items: center;
  background-color: #f0f3fa;
  border-radius: 10px;
  padding: 15px;
  width: 100%;
  height: 100px;
}

.card-content {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.card-icon img {
  width: 32px;
  height: 32px;
}

.card-details {
  display: flex;
  align-items: center;
  gap: 8px;
  height: 46px;
  font-weight: 500px;
}

.card-title {
  font-size: 15px;
  color: #000000;
  height: 25px;
}

.card-number {
  font-size: 28px;
  font-weight: bold;
  color: #000;
}
@media screen and (max-width: 480px) {
  .card {
    height: 70px;
    width: auto;
  }
}
</style>
