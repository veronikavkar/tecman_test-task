<template>
  <div class="header">
    <h1 class="header-title">Главная</h1>
    <div class="cards-container">
      <Card
        title="Сервисные компании"
        number="15"
        icon="company.svg"
        cardClass="service-card"
      />
      <Card
        title="Клиенты"
        number="132"
        icon="user.svg"
        cardClass="clients-card"
      />
      <Card
        title="Устройства"
        number="189"
        icon="devices.svg"
        cardClass="devices-card"
      />
    </div>
  </div>
</template>

<script>
import Card from "../components/common/Card.vue";

export default {
  components: {
    Card,
  },
};
</script>

<style scoped>
.header {
  display: flex;
  flex-direction: column;
}
.header-title {
  font-size: 20px;
  margin-bottom: 15px;
}

.cards-container {
  display: flex;
  justify-content: space-between;
  gap: 12px;
}

.service-card {
  background-color: #e8ecf5;
}

.clients-card {
  background-color: #fce4ec;
}

.devices-card {
  background-color: #e8ecf5;
}
</style>
