<template>
  <div class="search-input">
    <img :src="iconPath" alt="Search" />

    <input
      type="text"
      v-model="searchQuery"
      @input="onSearch"
      placeholder="Поиск"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
    };
  },
  computed: {
    iconPath() {
      return require(`@/assets/icons/search.svg`);
    },
  },
  methods: {
    onSearch() {
      this.$emit("search", this.searchQuery);
    },
  },
};
</script>

<style scoped>
.search-input {
  display: flex;
  border-bottom: 1px solid #c4c4c4;
  height: 27px;
}

input {
  border: none;
  font-size: 16px;
}
input::placeholder {
  color: #565e76;
}
img {
  margin-right: 8px;
  cursor: pointer;
  width: 17px;
}
@media screen and (max-width: 590px) {
  img {
    width: 16px;
  }
  input {
    font-size: 14px;
  }
}
</style>
