<template>
  <v-app>
    <v-container>
      <router-view />
    </v-container>
  </v-app>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-weight: bold;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background:#f0ffff;

  a {
    color: #2c3e50;
    text-decoration: none;
  }
}

#nav {
  padding: 30px;

  .router-link-exact-active {
    color: #42b983;
  }
}
</style>
