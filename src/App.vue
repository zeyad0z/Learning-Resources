<template>
  <the-header title="Learning Resources"></the-header>
  <Toggle></Toggle>
</template>

<script>
import Toggle from "./components/Toggle.vue";
import TheHeader from "./components/UI/TheHeader.vue";

export default {
  components: {
    TheHeader,
    Toggle,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
}
</style>
