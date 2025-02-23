<template>
  <div id="app">
    <TheHeader></TheHeader>

    <main class="main-content container">
      <header>
        <h1>Картины эпохи Возрождения</h1>
      </header>
    </main>
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
  --white: #fff;
  --black: #343030;
  --gray: #E1E1E1;
  --color-accent: #403432;
}

body {
  margin: 0;
  padding: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
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

.container {
  max-width: 1216px;
  margin: 0 auto;
}

.main-content {
  margin-top: 45px;
}
</style>
