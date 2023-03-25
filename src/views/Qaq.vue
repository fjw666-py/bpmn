<script>
import { nextTick } from 'vue'

export default {

  data() {
    return {
      count: 0
    }
  },
  mounted() {
    this.count = 0;

  },
  methods: {
    increment() {
      this.count++
      console.log(this.count);
      nextTick(() => {
        // 访问更新后的 DOM
      })
    }
  }
}
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
