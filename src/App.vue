<template>
  <div id="nav">
    <h2>Cylinder Volume Calculator</h2>
  </div>
  <router-view />
</template>

<style lang="scss">
:root {
  --dark-blue: #3d405b;
  --orange: #e07a5f;
  --yellow: #F2CC8F;
}

body {
  height: 100vh;
  width: 100vw;
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: var(--dark-blue);
  display: flex;
  flex-direction: column;

  height: 100%;
  width: 100%;
}

#nav {
  background: var(--orange);
  padding: 12px;
  font-size: 1.2rem;
  color: white;

  h2 {
    padding: 0;
  }
}
</style>
