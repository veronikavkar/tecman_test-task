<template>
  <div class="main-layout">
    <Sidebar />
    <div class="content">
      <Header />
      <DataTable />
    </div>
  </div>
</template>

<script>
import Sidebar from "../components/Sidebar.vue";
import Header from "../components/Header.vue";
import DataTable from "../components/DataTable.vue";
export default {
  name: "MainLayout",
  components: {
    Sidebar,
    Header,
    DataTable,
  },
};
</script>

<style scoped>
.main-layout {
  display: flex;
  margin: 16px 24px;
}

.content {
  margin-left: 72px;
  width: calc(100% - 72px);
  display: flex;
  flex-direction: column;
  gap: 12px;
}
@media screen and (max-width: 590px) {
  .main-layout {
    margin: 16px 10px;
  }
  .content {
    width: 100%;
    margin-right: 5px;
  }
}
@media screen and (max-width: 470px) {
  .content {
    margin-left: 50px;
  }
}
</style>
