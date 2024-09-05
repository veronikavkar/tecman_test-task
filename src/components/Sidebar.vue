<template>
  <div class="sidebar">
    <ul class="list">
      <li class="list-item" v-for="(icon, index) in icons" :key="index">
        <img
          class="list-icon"
          :src="getIconPath(icon.filename)"
          :alt="icon.name"
        />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Side-bar",
  data() {
    return {
      icons: [
        { name: "Logo", filename: "logo.svg" },
        { name: "Home", filename: "home.svg" },
        { name: "Companies", filename: "company.svg" },
        { name: "Users", filename: "user.svg" },
        { name: "Devices", filename: "devices.svg" },
        { name: "Settings", filename: "settings.svg" },
        { name: "Logs", filename: "logs.svg" },
        { name: "Profile", filename: "profile.svg" },
        { name: "Logout", filename: "exit.svg" },
      ],
    };
  },
  methods: {
    getIconPath(filename) {
      return require(`@/assets/icons/${filename}`);
    },
  },
};
</script>

<style scoped>
.sidebar {
  position: fixed;
  top: 0;
  left: 0;
  width: 72px;
  background-color: #e8ecf5;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}

.list {
  list-style: none;
  width: 100%;
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.list-item {
  width: 100%;
  height: 56px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.list-icon {
  width: 24px;
  height: auto;
}

.list-item:first-child .list-icon {
  width: 36px;
  height: auto;
}

.list-item:last-child {
  margin-top: auto;
}
@media screen and (max-width: 470px) {
  .sidebar {
    width: 50px;
  }
  .list-icon {
    width: 20px;
  }
}
</style>
