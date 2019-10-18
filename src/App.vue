<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
html {
  font-size: 10px;
  margin: 0;
  padding: 0;
}

body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #4f4f4f;
  background: radial-gradient(ellipse at center, #fff 0%, #fff 10%, #ccc 10%);
  background-size: 7rem 7rem;
  background-repeat: repeat;
  background-position: .5rem center;
  min-height: 100vh;
  margin: 0;
  padding: 0;
}
</style>
