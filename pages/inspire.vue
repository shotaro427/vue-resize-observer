<template>
  <v-col justify="center" align="center">
    <p class="height-text">height : {{ height }}</p>
    <div ref="text-card" class="text-card">
      <p class="text">{{ text }}</p>
    </div>
  </v-col>
</template>
<script>
export default {
  data() {
    return {
      text: 'hogehoge',
      height: 0,

      // Resize Observer Instance
      ro: null,
    }
  },
  async mounted() {
    this.onResized()
    this.ro = new ResizeObserver(this.onResized)
      .observe(this.$refs['text-card'])

    // fetch data
    const data = await this.fetchData()
    this.text = data
  },
  beforeDestroy() {
    if (this.ro) {
      this.ro.this.ro.unobserve(this.$refs['text-card'])
    }
  },
  methods: {
    onResized() {
      this.height = this.$refs['text-card'].getBoundingClientRect().height
    },
    fetchData() {
      return new Promise((resolve) => {
        setTimeout(() => {
          resolve('Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.')
        }, 2000);
      })
    }
  }
}
</script>
<style lang="scss" scoped>
.height-text {
  margin-top: 200px;
}
.text-card {
  width: 200px;
  background-color: grey;

  .text {
    margin-bottom: 0;
    padding: 4px;
  }
}
</style>
