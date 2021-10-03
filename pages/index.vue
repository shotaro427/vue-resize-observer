<template>
  <v-row justify="center" align="center">
    <v-card class="text-card">
      <p class="text">{{ text }}</p>
    </v-card>
  </v-row>
</template>
<script>
export default {
  data() {
    return {
      text: 'hogehoge'
    }
  },
  mounted() {
    setTimeout(() => {
      this.text = 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.'
    }, 2000);
  }
}
</script>
<style lang="scss" scoped>
.text-card {
  width: 200px;
  margin-top: 200px;

  .text {
    margin-bottom: 0;
    padding: 4px;
  }
}
</style>
