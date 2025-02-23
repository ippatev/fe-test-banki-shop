<template>
  <div id="app">
    <TheHeader></TheHeader>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';

export default {
  name: 'App',
  components: {
    TheHeader
  }
}
</script>

<style>
:root {
  --black: #343030;
}

#app {
  font-family: Merriweather, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--black);
  font-size: 14px;
}

h1 {
  font-size: 24px;
  font-weight: bold;
}

h2 {
  font-size: 18px;
  font-weight: normal;
}

h3 {
  font-size: 16px;
  font-weight: bold;
}

h4,
h5,
h6 {
  font-size: 14px;

}

h4 {
  font-weight: bold;
}

h5 {
  font-weight: bold;
}

h6 {
  font-weight: lighter;
}
</style>
