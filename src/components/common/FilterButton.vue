<template>
  <div class="filter-button" @click="onClick">
    <img :src="iconPath" :alt="label" />
    <span>{{ label }}</span>
    <div v-if="filterCount" class="filter-count">{{ filterCount }}</div>
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: true,
    },
    icon: {
      type: String,
      required: true,
    },
    filterCount: {
      type: Number,
      default: 0,
    },
    onClickAction: {
      type: Function,
      required: true,
    },
  },
  computed: {
    iconPath() {
      return require(`@/assets/icons/${this.icon}`);
    },
  },
  methods: {
    onClick() {
      this.onClickAction();
    },
  },
};
</script>

<style scoped>
.filter-button {
  display: flex;
  align-items: center;
  cursor: pointer;
}

img {
  margin-right: 8px;
  width: 22px;
}

span {
  color: #a53863;
  font-weight: bold;
}

.filter-count {
  background-color: #a53863;
  color: white;
  font-weight: bold;
  padding: 2px 6px;
  border-radius: 50%;
  margin-left: 5px;
}
@media screen and (max-width: 590px) {
  img {
    width: 15px;
  }
  span {
    font-size: 14px;
  }
}
</style>
