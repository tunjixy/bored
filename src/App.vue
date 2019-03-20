<template>
  <div id="app">
    <Home />
  </div>
</template>

<script>
import Home from "@/views/Home";
export default {
  components: {
    Home
  }
};
</script>


<style lang="scss">
#app {
  font-family: "Quicksand", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
*,
*::before,
*::after {
  box-sizing: border-box;
}

html {
  font-size: 100%;
}
</style>
