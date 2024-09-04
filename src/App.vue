<template>
  <div class="main-content">
    <MainLayout />
  </div>
</template>

<script>
import MainLayout from "./layouts/MainLayout.vue";
export default {
  name: "App",
  components: {
    MainLayout,
  },
};
</script>
<style>
body {
  font-family: "Inter", sans-serif;
}
</style>
