<template>
  <div class="overlay" @click="$emit('close')">
    <div class="modal">
      <div class="head">
        <div class="header">Ошибка</div>
        <div class="close-btn" @click="$emit('close')">×</div>
      </div>

      <div class="content">
        <div class="label firstBlock">Дата и время</div>
        <div class="dynamicText">{{ data.dateTime }}</div>
        <div class="label">Ошибка</div>
        <div class="dynamicText">{{ data.errorText }}</div>
        <div class="label">Контроллер</div>
        <div class="dynamicText linkText">{{ data.device }}</div>
        <div class="label">Сервисная компания</div>
        <div class="dynamicText linkText">{{ data.serviceCompany }}</div>
        <div class="label">Телефон для связи</div>
        <div class="dynamicText">{{ data.phone }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SideModal",
  props: {
    data: {
      type: Object,
      default: () => ({}),
    },
  },
};
</script>

<style scoped>
.overlay {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: flex-end;
  align-items: flex-start;
}
.head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 44px;
  padding: 0px 12px;
}
.modal {
  width: 400px;
  height: 100%;
  background-color: white;
  padding: 0;
  box-shadow: -2px 0 10px rgba(0, 0, 0, 0.2);
}
.close-btn {
  cursor: pointer;
  font-size: 24px;
  color: #565e76;
}
.header {
  font-size: 18px;
  font-weight: bold;
  display: flex;
  align-items: center;
}

.content {
  padding: 0 12px;
}

.label {
  display: block;
  color: #565e76;
  font-size: 12px;
  height: 12px;
  margin-top: 16px;
  margin-bottom: 5px;
}

.dynamic-text {
  font-size: 16px;
  height: 27px;
  margin-bottom: 0;
}

.linkText {
  color: #0072c0;
  cursor: pointer;
}

.linkText:hover {
  text-decoration: underline;
}

.first-block {
  margin-top: 21px;
}
</style>
