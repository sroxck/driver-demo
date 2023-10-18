<!--
 * @Author: sroxck
 * @Date: 2023-10-18 09:53:04
 * @LastEditors: sroxck
 * @LastEditTime: 2023-10-18 10:11:38
 * @Description: 
-->
<script setup lang="ts">
import driverPage from './components/driver.vue'
</script>

<template>
  <driverPage />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
