<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/cat-ratings">Cat ratings</router-link>|
      <router-link to="/about">About</router-link>
    </div>
    <font-awesome-icon icon="heart" />
    <router-view />
  </div>
</template>

<style lang="scss">
* {
  background-color: darkslateblue;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: lavender;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: lavender;
    margin-right: 5px;

    &.router-link-exact-active {
      color: plum;
    }
  }
}
</style>
