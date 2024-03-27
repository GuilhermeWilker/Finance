<script setup></script>

<template>
  <header>
    <nav>
      <menu>
        <router-link to="/newgain">Nova entrada</router-link>
        <router-link to="/">Dashboard</router-link>
        <router-link to="/newincome">Nova saída</router-link>
      </menu>
    </nav>
  </header>
</template>

<style scoped>
header {
  box-shadow: 0px 2px 5px 0px rgba(0, 0, 0, 0.75);
  padding: 2em 4em;
}

nav {
  margin: 0 auto;
}

menu {
  display: flex;
  align-items: center;
  justify-content: space-between;

  font-size: 1em;
}
</style>
