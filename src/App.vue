<template>
  <div id="app">
    <Home />
  </div>
</template>

<script>
import Home from '@/views/Home'
export default {
  components: {
    Home
  }
}
</script>

<style lang="scss">
@import "./assets/scss/variables.scss";
*,
*::before,
*::after {
  box-sizing: border-box;
}
body {
  background-color: $body-bg;
}
html {
  font-size: 100%;
  font-family: "Quicksand", sans-serif;
}
</style>
