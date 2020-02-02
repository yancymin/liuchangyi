/**
 * @author Yancy Min
 * @email me@yancymin.design
 * @create date 2020-02-02 18:34:01
 * @modify date 2020-02-02 18:34:01
 * @desc [description]
 */
<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
@import './style/reset.css';

#app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
    Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #000;
}

body {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  background: #070707;
}

@media screen and (max-width: 500px) {
  body {
    overflow-x: hidden;
    overflow-y: auto;
  }
}
</style>
