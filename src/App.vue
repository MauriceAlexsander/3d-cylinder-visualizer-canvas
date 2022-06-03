<template>
  <div id="nav">
    <h2>Cylinder Volume Calculator</h2>
  </div>
  <router-view />
</template>

<style lang="scss">
body {
  height: 100vh;
  width: 100vw;
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #3d405b;
  display: flex;
  flex-direction: column;

  height: 100%;
  width: 100%;
}

#nav {
  background: #e07a5f;
  padding: 12px;
  font-size: 1.2rem;
  color: white;

  h2 {
    padding: 0;
  }
}
</style>
